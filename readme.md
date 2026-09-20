# Projeto PDS — LaTeX

Repositório do relatório do projeto da disciplina **Processamento Digital de Sinais I (EEL7825)** da Universidade Federal de Santa Catarina (UFSC).

O projeto aborda o desenvolvimento de um sistema para **rastreamento da posição de jogadores de futebol a partir de imagens**, utilizando técnicas de processamento digital de sinais e visão computacional.

## 📌 Sobre o projeto

A proposta consiste em desenvolver uma aplicação capaz de receber um vídeo de uma partida de futebol e processar seus quadros para estimar a posição dos jogadores no campo e associá-los às respectivas equipes.

O trabalho utiliza como referência o conjunto de dados **SoccerTrack v2**, que disponibiliza vídeos de partidas completas e informações de referência sobre os jogadores, incluindo suas posições no campo, identificadores, números das camisas e equipes.

Um dos aspectos centrais do projeto é a transformação das coordenadas observadas na imagem para um sistema de coordenadas associado ao campo, utilizando informações geométricas da câmera e técnicas como **homografia**.

Este repositório contém o documento LaTeX utilizado para a elaboração e documentação do projeto.

---

## 📁 Estrutura do repositório

A estrutura atual do projeto é:

```text
ProjetoPDS-LaTex/
├── .gitignore
├── capa.tex
├── introducao.tex
├── main.tex
├── media/
│   └── brasao_UFSC.png
└── readme.md
```

### `main.tex`

É o arquivo principal do documento.

Ele é responsável por:

* definir a classe do documento;
* configurar margens;
* importar os pacotes LaTeX utilizados;
* configurar opções de gráficos;
* incluir os diferentes componentes do relatório.

Atualmente, o documento possui a seguinte estrutura:

```text
main.tex
├── capa.tex
└── introducao.tex
```

Novas seções do relatório devem ser adicionadas preferencialmente através de arquivos `.tex` separados e incluídas no `main.tex` utilizando `\input{}`.

---

### `capa.tex`

Contém a página de capa do trabalho.

A capa inclui:

* identificação da disciplina;
* título do projeto;
* autores;
* números de matrícula;
* localização;
* ano;
* brasão da UFSC.

O brasão utilizado está localizado em:

```text
media/brasao_UFSC.png
```

---

### `introducao.tex`

Contém a seção de introdução do relatório.

A introdução apresenta:

* o contexto da análise computacional de partidas de futebol;
* a utilização de processamento digital de sinais e visão computacional;
* os desafios relacionados ao processamento de vídeos de futebol;
* o conceito de Game State Reconstruction (GSR);
* a utilização de homografia;
* o conjunto de dados SoccerTrack v2;
* os objetivos gerais da proposta.

---

### `media/`

Diretório destinado aos recursos visuais utilizados pelo documento.

Atualmente contém:

```text
media/
└── brasao_UFSC.png
```

Novas imagens utilizadas no relatório devem ser armazenadas nesse diretório.

---

### `.gitignore`

O projeto utiliza `.gitignore` para evitar que arquivos gerados pelo ambiente de desenvolvimento sejam versionados.

Atualmente são ignorados:

```text
/.vscode
/build
```

O diretório `/build` é destinado aos arquivos gerados durante o processo de compilação.

---

# 🛠️ Developer Guide

Esta seção descreve o ambiente necessário para desenvolver e compilar o documento.

## Ferramentas utilizadas

O projeto utiliza principalmente:

| Ferramenta     | Função                                    |
| -------------- | ----------------------------------------- |
| LaTeX          | Sistema de composição do documento        |
| `pdflatex`     | Compilador utilizado para gerar o PDF     |
| VS Code        | Editor recomendado                        |
| LaTeX Workshop | Extensão recomendada para desenvolvimento |
| Git            | Controle de versão                        |
| GitHub         | Hospedagem do repositório                 |

---

## LaTeX

O relatório é escrito em **LaTeX**.

O arquivo principal utiliza:

```latex
\documentclass[a4paper,12pt]{article}
```

Portanto, o documento utiliza a classe padrão `article`, com:

* papel A4;
* tamanho de fonte de 12 pt.

---

## Pacotes utilizados

Atualmente, `main.tex` utiliza os seguintes pacotes:

```latex
\usepackage[a4paper, top=2cm, bottom=2.5cm, left=2.5cm, right=2cm]{geometry}
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage{float}
\usepackage{caption}
\usepackage{tabularx}
\usepackage{booktabs}
\usepackage{multirow}
\usepackage[utf8]{inputenc}
\usepackage{longtable}
\usepackage{pgfplots}
```

O `pgfplots` está configurado com:

```latex
\pgfplotsset{compat=1.18}
```

Esses pacotes fornecem suporte, entre outras coisas, para:

* configuração de margens;
* equações matemáticas;
* inclusão de imagens;
* posicionamento de figuras;
* legendas;
* tabelas;
* tabelas de maior extensão;
* geração de gráficos.

---

# ⚙️ Configuração do ambiente

## Linux

Em distribuições baseadas em Debian/Ubuntu, pode-se instalar uma distribuição LaTeX através do TeX Live:

```bash
sudo apt update
sudo apt install texlive-latex-base texlive-latex-extra
```

Para garantir que todos os pacotes necessários estejam disponíveis:

```bash
sudo apt install texlive-full
```

A segunda opção instala uma quantidade significativamente maior de pacotes e, consequentemente, requer mais espaço em disco.

Verifique a instalação com:

```bash
pdflatex --version
```

---

## Windows

No Windows, recomenda-se utilizar uma distribuição LaTeX como **MiKTeX** ou **TeX Live**.

Após a instalação, verifique se o comando abaixo está disponível no terminal:

```bash
pdflatex --version
```

---

## macOS

No macOS, pode-se utilizar o **MacTeX**, que fornece uma distribuição LaTeX completa.

Após a instalação:

```bash
pdflatex --version
```

---

# 📝 Desenvolvimento com VS Code

O editor recomendado para o projeto é o **Visual Studio Code**.

A extensão recomendada é:

**LaTeX Workshop**

Ela fornece recursos como:

* compilação do documento;
* visualização do PDF;
* atualização automática;
* autocomplete de comandos LaTeX;
* navegação entre código e PDF;
* visualização de erros de compilação.

Após instalar a extensão, abra a raiz do projeto:

```bash
code ProjetoPDS-LaTex
```

O arquivo principal a ser editado é:

```text
main.tex
```

---

# 🔨 Processo de build

Atualmente o projeto não possui um `Makefile` ou outro sistema de automação de build.

A compilação é realizada diretamente utilizando `pdflatex`.

A partir da raiz do projeto:

```bash
pdflatex -output-directory=build main.tex
```

Isso gera o PDF em:

```text
build/main.pdf
```

O diretório `build/` é ignorado pelo Git através do `.gitignore`.

---

## Build no VS Code

Com a extensão **LaTeX Workshop** instalada, também é possível compilar o projeto diretamente pelo editor.

Abra:

```text
main.tex
```

e utilize o comando de build da extensão.

Por padrão, a extensão pode gerar os arquivos auxiliares no diretório do projeto. Caso seja desejado manter todos os artefatos dentro de `build/`, a configuração do LaTeX Workshop deve ser ajustada para utilizar esse diretório como `outDir`.

Uma configuração possível no `.vscode/settings.json` é:

```json
{
    "latex-workshop.latex.outDir": "%DIR%/build"
}
```

Como `.vscode/` já está incluído no `.gitignore`, essa configuração pode ser mantida localmente sem ser adicionada ao repositório.

# ➕ Adicionando novas seções

Cada seção relevante do relatório deve preferencialmente ser mantida em seu próprio arquivo `.tex`.

Por exemplo, para adicionar uma seção de metodologia:

```text
ProjetoPDS-LaTex/
├── capa.tex
├── introducao.tex
├── metodologia.tex
├── main.tex
└── media/
```

No `main.tex`, adicione:

```latex
\input{metodologia}
```

A estrutura ficará:

```latex
\begin{document}

\input{capa}
\input{introducao}
\input{metodologia}

\end{document}
```

Essa organização evita que `main.tex` fique excessivamente grande e facilita o desenvolvimento colaborativo.


# 🚧 Próximas extensões

Conforme o relatório evoluir, a estrutura poderá ser expandida para incluir:

```text
ProjetoPDS-LaTex/
├── .gitignore
├── capa.tex
├── introducao.tex
├── metodologia.tex
├── resultados.tex
├── conclusao.tex
├── main.tex
├── media/
│   ├── brasao_UFSC.png
│   └── ...
└── readme.md
```

Também podem ser adicionados posteriormente:

* referências bibliográficas;
* gerenciamento automático de bibliografia com `biblatex` e `biber`;
* `latexmk`;
* `Makefile`;
* configuração compartilhada do LaTeX Workshop;
* pipeline de CI para compilação automática do PDF.

Essas ferramentas devem ser introduzidas conforme a complexidade do documento aumentar, evitando adicionar dependências desnecessárias ao projeto em seu estado atual.

---

# 📄 Licença

Este repositório contém o material desenvolvido para fins acadêmicos na disciplina **Projeto Nível II em Controle e Processamento de Sinais I (EEL7825)**.
