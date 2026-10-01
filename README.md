# GAP · Gerador de Assinatura de E-mail

Gerador oficial da assinatura de e-mail da **GAP SSMA**. Funciona direto no navegador (sem login e sem servidor).
Os dados digitados ficam só no computador de quem usa: nada é enviado ou salvo.

**Link para os colaboradores:** https://gap-ssma.github.io/gap-assinatura-email/

## Conteúdo

| Caminho | Descrição |
|---|---|
| `index.html` | Gerador (versões, formulário, pré-visualização, *Copiar assinatura*, *Baixar .htm*, instruções) |
| `assets/gap_logo.png` | Logo GAP (versão Padrão) — 262×60 px, exibido em 131×30 |
| `assets/gap_18anos.png` | Selo GAP 18 anos — 171×58 px, exibido em 128×43 |
| `assets/selo_gptw.png` | Selo Great Place to Work (Jun/2026–Jun/2027) — 76×130 px, exibido em 38×65 |
| `assets/gap_sistemas.png` | Logo GAP Sistemas — 354×90 px, exibido em 87×22 |

As assinaturas coladas no Outlook/Gmail apontam para
`https://gap-ssma.github.io/gap-assinatura-email/assets/<arquivo>.png`.
**Não renomeie, não mova e não apague os arquivos de `assets/`**: assinaturas já instaladas deixariam de mostrar os logos.
Para trocar uma imagem mantendo o mesmo visual, substitua o arquivo com o **mesmo nome** e a mesma proporção.

## Versões da assinatura

As versões ficam no array `VERSOES` no início do `<script>` de `index.html`:

```js
{ id: "18anos", label: "GAP 18 anos", descricao: "Comemorativa · válida até 31/12/2026",
  logo: "gap_18anos", selo: "selo_gptw", validaDe: null, validaAte: "2026-12-31", destaque: true, template: "colunas" }
```

- `logo` / `selo`: chaves do objeto `IMAGENS` (arquivo + tamanho de exibição + texto alternativo). `selo: null` remove o selo.
- `validaDe` / `validaAte` (`AAAA-MM-DD`, opcionais): fora do período a versão aparece como *expirada* e não pode ser escolhida.
- `destaque: true`: vem selecionada por padrão enquanto estiver válida (senão, a primeira versão válida).
- `template`: chave do objeto `TEMPLATES` (hoje só `colunas`). Para um layout novo, crie outra função em `TEMPLATES`.

**Nova versão (ex.: campanha 2027):** adicione o PNG em `assets/` (2× o tamanho de exibição), registre-o em `IMAGENS`,
adicione um item em `VERSOES` e faça o commit. O GitHub Pages publica em ~1 minuto.

**Selo GPTW novo (ex.: Jun/2027–Jun/2028):** substitua `assets/selo_gptw.png` (mesmo nome, 76×130 px) — as assinaturas
já instaladas passam a mostrar o selo novo automaticamente. A origem é `https://www.gapgestao.com.br/assets/selo-gptw.svg`
(SVG não aparece em e-mail, por isso é convertido para PNG).

Link direto para uma versão: `?versao=padrao` ou `?versao=18anos`.

## Histórico

- **v2 (out/2026):** versões *Padrão* e *GAP 18 anos*; selo GPTW 2026–2027; logos hospedados no GitHub Pages;
  fallback com imagens embutidas quando sem internet.
- **v1 (out/2026):** assinatura GAP 18 anos aprovada (layout em tabelas, Arial, compatível com Outlook/Gmail/webmail).
