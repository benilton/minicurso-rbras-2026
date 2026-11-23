# Minicurso da 70ª RBras: agrupamento de células e expressão diferencial em célula única

Página do minicurso: <https://benilton.github.io/minicurso-rbras-2026/>

Este repositório guarda a página pública do minicurso, apresentado na sala 253 do IMECC/UNICAMP em 23 e 24 de novembro de 2026. A página entrega os slides dos dois encontros e os links dos notebooks no Google Colab. O site é feito em Quarto e publicado no GitHub Pages por GitHub Actions a cada push na branch `main`.

Docente: Benilton S Carvalho (IMECC/UNICAMP). Os notebooks derivam do Módulo 04 do [scNotebooks](https://github.com/integrativebioinformatics/scNotebooks).

## Estrutura

| Caminho | Conteúdo |
|---|---|
| `index.qmd` | Apresentação do minicurso |
| `programa.qmd` | Programação dos dois encontros, bloco a bloco |
| `encontro-1.qmd`, `encontro-2.qmd` | Slides, links do notebook e pontos de verificação |
| `como-abrir.qmd` | Passo a passo de abertura no Colab |
| `slides/` | Slides renderizados (cópia de `minicurso-rbras/slides/*.html`) |
| `assets/` | Tema, fontes e imagens |
| `.github/workflows/publicar.yml` | Renderização e publicação no GitHub Pages |

## Publicação inicial

Os comandos abaixo criam o repositório público, ativam o GitHub Pages pelo GitHub Actions e enviam o conteúdo. Eles supõem o `gh` autenticado na conta `benilton`. O Pages precisa estar ativo antes do primeiro push, porque o push dispara a publicação.

```bash
cd ~/Documents/GitHub/minicurso-rbras-2026
git init -b main
git add .
git commit -m "Página do minicurso da 70ª RBras"
gh repo create benilton/minicurso-rbras-2026 --public --source=. --remote=origin
gh api -X POST repos/benilton/minicurso-rbras-2026/pages -f build_type=workflow
git push -u origin main
gh run watch
```

Sem o `gh`, crie o repositório público pelo site do GitHub e use `git remote add origin` seguido de `git push -u origin main`. Depois abra Settings, Pages e escolha "GitHub Actions" em Source. Se a primeira execução falhar por falta do Pages, use o botão "Re-run jobs" na aba Actions.

## Atualização

Para trocar os slides, copie de novo os arquivos `encontro1.html` e `encontro2.html` de `minicurso-rbras/slides/` para `slides/` e faça commit e push. Para conferir o site antes do push, use `quarto preview` nesta pasta. A pasta `_site/` é gerada pelo Quarto e fica fora do repositório.
