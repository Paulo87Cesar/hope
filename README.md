# Nexo TI — Site institucional

Site moderno e focado em conversão para a **Nexo TI**, empresa de suporte de TI,
redes e automação de Paulo César de Oliveira — Hortolândia/SP.

Estrutura inspirada (com conteúdo 100% reescrito para a Nexo TI) em dois sites de
field services de TI: **Computero** (narrativa "o que é field service" + lista ampla
de serviços) e **Infraspine** (faixa de estatísticas, "por que suporte lento custa
caro", tabela de resumo do serviço, FAQ e CTA final).

## Estrutura

| Arquivo | O que é |
|---|---|
| `site-pwc/` | **Clone final (recomendado)**: site estático gerado pelo Perfect Web Clone (pwc) — React + Vite + Tailwind, mesclando os dois sites de referência com o conteúdo da Nexo TI |
| `index.html` | Versão anterior da landing (HTML/CSS puro) — mantida como referência |
| `blog.html` | 3 artigos SEO: computador lento, Wi-Fi caindo, Active Directory (também dentro de `site-pwc/`) |
| `css/style.css`, `js/main.js`, `assets/` | Design system da versão HTML pura |
| `.pwc/` | Dados da ferramenta Perfect Web Clone: extrações (`sources/`), sandbox de build (`sandboxes/`) e resultado do build (`build-result.json`) |
| `robots.txt`, `sitemap.xml` | SEO técnico |
| `plano-de-negocio.md` | Resumo do modelo de negócio e estratégia de marketing |

## O site clonado (`site-pwc/`)

Construído com a ferramenta **Perfect Web Clone** (`python -m pwc`) que você instalou:

1. `pwc clone` capturou os dois sites (screenshots, HTML, DOM, CSS e assets) — guardados em `.pwc/sources/`;
2. o planejador dividiu a página do Infraspine em 8 seções (nav, breadcrumb, hero com estatísticas, "por que", 8 frentes de serviço, FAQ, CTA + planos, rodapé);
3. eu escrevi os 8 componentes React com o conteúdo mesclado da Nexo TI (estrutura Infraspine + narrativa field services do Computero + planos do site anterior);
4. `pwc assemble` + `pwc build` geraram o `dist` estático — resultado final em `site-pwc/`.

Para visualizar: **basta dar dois cliques em `site-pwc\index.html`** — o bundle é de arquivo único
(`vite-plugin-singlefile`), então funciona aberto direto do disco. Opcionalmente, sirva via HTTP:

```powershell
cd C:\Users\pc30r\Desktop\empresa\site-pwc
python -m http.server 8080   # depois abra http://localhost:8080
```

Para publicar: envie o conteúdo de `site-pwc/` para Netlify/Vercel/GitHub Pages.

Para rebuildar após editar os componentes:
```powershell
$env:PWC_SOURCES_DIR = "C:\Users\pc30r\Desktop\empresa\.pwc\sources"
$env:PWC_SANDBOX_DIR = "C:\Users\pc30r\Desktop\empresa\.pwc\sandboxes"
python .pwc\driver_assemble_build.py
```
> Nota: os limites do gate de integridade do pwc foram ajustados (com sua aprovação) em
> `AppData\Roaming\Python\Python314\site-packages\core\capture_integrity.py` — os valores originais
> estão comentados ao lado de cada constante para reversão.

## Fotos do site

As fotos usadas nas seções são **royalty-free (Unsplash License / Pexels License)** — livres para uso
comercial, sem atribuição obrigatória. Não usamos as fotos da Computero/Infraspine (protegidas por direitos
autorais). Créditos (para rastreabilidade):

- `narrativa.jpg` — Pexels 7639370 (mãos fazendo manutenção em notebook) — indicada pelo usuário
- `servico-1.jpg` — Pexels 17489152 (tecnologia/escritório) — indicada pelo usuário
- `servico-2.jpg` — Pexels 1181675 (pessoa digitando no laptop) — indicada pelo usuário
- `servico-3.jpg` — Pexels 31854238 (manutenção de computador) — indicada pelo usuário
- `servico-4.jpg` — Unsplash photo-1522071820081-009f0129c71c
- `servico-5.jpg` — Unsplash photo-1612815154858-60aa4c59eaa6
- `servico-6.jpg` — Pexels 990423 — indicada pelo usuário
- `servico-7.jpg` — Pexels 2881224 (cabos ethernet / switch de rede) — indicada pelo usuário
- `servico-8.jpg` — Pexels 35147150 (armazenamento de dados) — indicada pelo usuário

Para trocar uma foto, substitua o arquivo em
`.pwc\sandboxes\sandbox-44fcbe9fc013\public\assets\images\photos\` (mesmo nome) e rode
`python .pwc\driver_rebuild_verify.py`.

## Como publicar (gratuito)

1. **Vercel/Netlify:** arraste a pasta `empresa` para o painel (arrastar e soltar) — o site sobe em ~1 minuto.
2. **GitHub Pages:** crie um repositório, envie os arquivos e ative Pages em *Settings → Pages*.
3. Site estático: funciona em qualquer hospedagem, sem banco de dados.

## ⚠️ Antes de divulgar, personalize

1. **Foto real** — substitua o bloco monograma "PC" na seção Sobre (`index.html`, procure por `about-photo`) por sua foto.
   As pesquisas de conversão mostram que foto real aumenta muito a confiança.
2. **Depoimentos** — quando tiver clientes atendidos, adicione depoimentos reais no local indicado por comentário
   em `index.html`. **Nunca** publique depoimentos fictícios.
3. **Preços** — os valores dos planos (R$ 89 / R$ 149 / R$ 249) são referências de mercado. Ajuste em `index.html`
   na seção `pricing-grid` antes de publicar, se preferir.
4. **Domínio** — troque `https://nexoti.com.br` pelo domínio real em `index.html` (Open Graph e JSON-LD),
   `robots.txt` e `sitemap.xml`. Verifique disponibilidade e faça busca no INPI antes de registrar a marca "Nexo TI".
5. **CNPJ / dados formais** — quando abrir o MEI/ME, adicione razão social e CNPJ no rodapé.
6. **Agendamento automático** — quando quiser, troque o CTA do diagnóstico por um link do **Calendly** (versão
   gratuita) para o cliente escolher o horário sozinho. A pesquisa de conversão mostra que calendário converte
   mais que formulário.
7. **Horário de atendimento** — ajuste o prometido no FAQ se o seu horário real for diferente.

## Dados de contato já configurados (retirados do seu currículo)

- WhatsApp: (19) 99592-6405 → todos os botões já abrem conversa com mensagem pronta
- E-mail: pc30rock@gmail.com
- LinkedIn: linkedin.com/in/paulo-oliveira-800a441b8 · GitHub: github.com/Paulo87Cesar
- Portfólio: paulodeveloper.site

## Boas práticas aplicadas (baseadas em pesquisa de conversão de MSPs)

- Headline específica: diz **para quem** é o serviço (empresas de Hortolândia/Campinas)
- **Um único CTA primário** em todo o site: "Agendar diagnóstico gratuito" → WhatsApp
- Próximos passos explícitos (seção "4 passos"): o visitante sabe o que acontece depois do contato
- Prova social real (empresas, trajetória, certificação TrendsIT/Softex, pós em IA) — nada inventado
- WhatsApp como canal principal + botão flutuante com mensagem pré-preenchida
- SEO local (títulos/meta para "suporte de TI Hortolândia", "manutenção Campinas") + JSON-LD (LocalBusiness e FAQPage)
- Blog com conteúdo útil para atrair tráfego orgânico
