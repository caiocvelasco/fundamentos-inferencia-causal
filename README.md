# Fundamentos para Inferência Causal

Este repositório contém as **Notas de Aula** do curso **Fundamentos para Inferência Causal**.

O conteúdo é desenvolvido como um [Quarto Book](https://quarto.org), com suporte nativo a Markdown, LaTeX, código e referências.

O curso é organizado de forma sequencial, começando por **Probabilidade** e avançando posteriormente para Inferência Estatística, Regressão e Inferência Causal.

As aulas do curso são ao vivo. Este livro funciona como material de apoio, estudo e consulta.

---

## Estrutura do Curso

A estrutura planejada é:

```text
Módulo 0 — Pré-curso de Matemática
Módulo 1 — Probabilidade
Módulo 2 — Inferência Estatística
Módulo 3 — Regressão
Módulo 4 — Inferência Causal
```

---

## Project Structure

A estrutura inicial do projeto é:

```text
.
|-- .quarto/
|-- .venv/
|-- README.md
|-- docs/                       # rendered HTML output
|-- _quarto.yml                 # main Quarto configuration
|-- chapters/                   # course chapters (.qmd files)
|   └── 01_modelos_probabilisticos.qmd
|-- index.qmd                   # book landing page
|-- references.bib              # bibliography
|-- requirements.txt            # Python dependencies
```

---

## Setup

### 1. Install the System Requirements

Instale:

- [Python](https://www.python.org/)
- [Quarto](https://quarto.org/docs/get-started/)
- [Git](https://git-scm.com/)

Verifique se estão disponíveis:

```bash
python --version
quarto --version
git --version
```

Essas ferramentas são instaladas no sistema.

As dependências Python específicas do projeto serão instaladas posteriormente dentro do ambiente virtual `.venv`.

---

### 2. Clone the Repository

```bash
git clone <repository-url>
cd <repository-name>
```

---

### 3. Create the Python Virtual Environment

```bash
python -m venv .venv
```

Ative o ambiente virtual.

#### Windows — Git Bash

```bash
source .venv/Scripts/activate
```

#### Windows — PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

#### macOS / Linux

```bash
source .venv/bin/activate
```

Quando ativado, o terminal normalmente mostrará:

```text
(.venv)
```

---

### 4. Install the Python Dependencies

Com `.venv` ativado:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Para conferir os pacotes instalados:

```bash
pip list
```

As dependências listadas em `requirements.txt` são instaladas apenas dentro do ambiente virtual do projeto.

---

## Quarto

### 5. Configure `_quarto.yml`

O arquivo `_quarto.yml` controla a estrutura e a aparência do livro.

A configuração inicial do projeto é semelhante a:

```yaml
project:
  type: book
  output-dir: docs

book:
  title: "Fundamentos para Inferência Causal"
  subtitle: "Notas de Aula"

  search: true

  sidebar:
    style: docked
    collapse-level: 1

  chapters:
    - index.qmd

    - part: "Módulo 1 — Probabilidade"
      chapters:
        - chapters/01_modelos_probabilisticos.qmd

format:
  html:
    theme: flatly

    toc: true
    toc-location: right
    toc-depth: 3

    code-link: true
    code-copy: true

    fontsize: 1.1em
    linestretch: 1.6

    grid:
      sidebar-width: 280px
      body-width: 950px
      margin-width: 280px
      gutter-width: 1.5rem

number-sections: false

lang: pt-BR
```

Novos capítulos devem ser adicionados ao diretório `chapters/` e incluídos em `_quarto.yml`.

---

### 6. Edit `index.qmd`

O arquivo `index.qmd` funciona como página inicial das notas.

Exemplo:

```markdown
---
title: "Fundamentos para Inferência Causal"
---

# Sobre estas notas

Estas são as notas de aula do curso **Fundamentos para Inferência Causal**.

O objetivo é construir, passo a passo, os fundamentos necessários para compreender Inferência Causal de forma rigorosa.

O curso percorre:

- Probabilidade
- Inferência Estatística
- Regressão
- Inferência Causal
```

---

## Writing Chapters

Cada capítulo é um arquivo `.qmd`.

Por exemplo:

```text
chapters/
└── 01_modelos_probabilisticos.qmd
```

Os arquivos Quarto suportam Markdown e matemática escrita em LaTeX.

Matemática inline:

```markdown
A esperança de uma variável aleatória é denotada por $E[X]$.
```

Equações em destaque:

```markdown
$$
E[X] = \sum_x x p_X(x)
$$
```

---

## Local Development

### 7. Preview Locally

Para iniciar o servidor local:

```bash
quarto preview
```

O Quarto mostrará uma URL local, normalmente algo como:

```text
http://localhost:xxxx
```

Alterações nos arquivos `.qmd` serão automaticamente renderizadas durante o preview.

---

### 8. Render the Book

Para gerar o site estático:

```bash
quarto render
```

O resultado será salvo em:

```text
docs/
```

---

## Publishing

### GitHub Pages

Como o projeto utiliza:

```yaml
output-dir: docs
```

o conteúdo renderizado pode ser publicado diretamente pelo GitHub Pages a partir da pasta:

```text
/docs
```

No GitHub:

```text
Settings
→ Pages
→ Build and deployment
→ Deploy from a branch
```

Selecione:

```text
Branch: main
Folder: /docs
```

Depois de cada atualização:

```bash
quarto render
git add .
git commit -m "Update course notes"
git push
```

O GitHub Pages publicará a nova versão do conteúdo.

---

## References

Referências bibliográficas podem ser armazenadas em:

```text
references.bib
```

e usadas diretamente nos arquivos `.qmd`.

---

## Development Notes

- Não versionar `.venv/`.
- Manter `.venv/` no `.gitignore`.
- Manter arquivos sensíveis, como `.env`, fora do Git.
- Criar cada novo capítulo dentro de `chapters/`.
- Atualizar `_quarto.yml` ao adicionar novos capítulos.
- Usar `quarto preview` durante a escrita.
- Usar `quarto render` antes de publicar alterações.

---

## Current Status

O desenvolvimento começa por:

```text
Módulo 1 — Probabilidade
└── Modelos Probabilísticos
```

Os demais módulos serão adicionados progressivamente conforme o curso for desenvolvido.
