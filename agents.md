# AGENTS.md

## 1. Contexto

Este repositório contém a documentação acadêmica do projeto:

**Sistema de rastreamento de posição de jogadores de futebol baseado em imagens**

O trabalho é desenvolvido no contexto da disciplina de **Processamento Digital de Sinais** e investiga técnicas de Processamento Digital de Imagens, Visão Computacional e rastreamento aplicadas a partidas de futebol.

O documento deve apresentar o projeto de forma acadêmica, técnica e reprodutível.

---

## 2. Objetivo deste repositório

Este repositório é responsável exclusivamente pela documentação em LaTeX do projeto.

O conteúdo deve contemplar, conforme a estrutura definida no trabalho:

* contextualização do problema;
* relevância da aplicação;
* objetivos;
* fundamentação teórica;
* métodos;
* metodologia proposta;
* dataset;
* experimentos;
* resultados;
* discussão;
* conclusões;
* referências.

O código-fonte dos experimentos pertence ao repositório do projeto de implementação e não deve ser duplicado neste repositório.

---

## 3. Estrutura do projeto

A estrutura real do repositório deve ser preservada.

Uma organização esperada é:

```text
ProjetoPDS-Latex/
├── main.tex
├── sections/
│   ├── introducao.tex
│   ├── objetivos.tex
│   ├── fundamentacao.tex
│   ├── metodos.tex
│   ├── resultados.tex
│   └── conclusao.tex
├── references/
│   └── references.bib
├── figures/
├── build/
├── README.md
└── AGENTS.md
```

Antes de criar, mover ou renomear arquivos, verificar a estrutura existente do repositório.

Não assumir que os nomes acima correspondem necessariamente aos arquivos atuais.

---

## 4. Arquivo principal

O arquivo principal do documento é:

```text
main.tex
```

O `main.tex` deve funcionar principalmente como arquivo de composição do documento.

Sempre que possível, conteúdo textual de seções deve permanecer em arquivos separados e ser incluído pelo arquivo principal.

Por exemplo:

```latex
\input{sections/introducao}
```

ou:

```latex
\include{sections/introducao}
```

Evitar colocar grandes blocos de texto diretamente no `main.tex`.

---

## 5. Compilação

Os arquivos auxiliares de compilação devem ser direcionados para:

```text
build/
```

A configuração do VS Code/LaTeX Workshop utiliza:

```json
{
    "latex-workshop.latex.outDir": "%DIR%/build"
}
```

Não alterar essa configuração sem necessidade.

O PDF final não deve ser gerado na raiz do projeto.

O arquivo PDF principal deve ser:

```text
build/main.pdf
```

O nome apresentado ao usuário pode ser configurado separadamente quando necessário, mas o processo de compilação deve continuar compatível com o fluxo existente.

---

## 6. LaTeX

Utilizar LaTeX de maneira idiomática e consistente.

Preferir:

* comandos semânticos;
* ambientes apropriados;
* referências cruzadas;
* bibliografia via BibTeX/Biber conforme a configuração existente;
* figuras vetoriais quando apropriado;
* tabelas com estrutura semântica.

Evitar formatação manual excessiva.

Por exemplo, preferir:

```latex
\section{Objetivos}
```

em vez de tentar reproduzir visualmente um título utilizando comandos de fonte.

---

## 7. Escrita acadêmica

O texto deve utilizar linguagem:

* formal;
* objetiva;
* técnica;
* impessoal;
* clara;
* consistente.

Evitar linguagem promocional ou afirmações exageradas.

Evitar frases como:

> O método proposto é extremamente eficiente e revolucionário.

Preferir formulações verificáveis, como:

> O método proposto é avaliado considerando métricas de detecção, rastreamento e erro de localização.

Afirmações quantitativas devem ser acompanhadas pelos resultados ou referências correspondentes.

---

## 8. Consistência terminológica

Utilizar terminologia consistente ao longo de todo o documento.

Termos importantes do projeto incluem:

* processamento digital de sinais;
* processamento digital de imagens;
* visão computacional;
* detecção de objetos;
* rastreamento de múltiplos objetos (MOT);
* reconstrução do estado do jogo (GSR);
* homografia;
* transformação de coordenadas;
* posição no campo;
* jogador;
* equipe;
* bounding box;
* frame;
* vídeo;
* dataset.

Quando uma sigla for introduzida, escrever primeiro o termo completo:

```latex
rastreamento de múltiplos objetos (Multi-Object Tracking -- MOT)
```

Depois disso, utilizar a sigla de maneira consistente.

---

## 9. Citações

Afirmações técnicas ou históricas relevantes devem possuir referências bibliográficas quando apropriado.

Exemplos de situações que normalmente exigem citação:

* descrição de datasets;
* definição de algoritmos;
* métodos de rastreamento;
* métodos de detecção;
* métricas;
* métodos de estimação de homografia;
* trabalhos anteriores;
* afirmações sobre o estado da arte.

Não inventar referências bibliográficas.

Quando uma referência não estiver disponível, pesquisar a fonte antes de adicioná-la ao documento.

---

## 10. Dataset

O projeto utiliza principalmente o:

**SoccerTrack v2 — Full-Pitch Soccer Dataset for Game State Reconstruction**

A descrição do dataset deve ser baseada na publicação ou documentação oficial correspondente.

Informações como:

* número de partidas;
* quantidade de frames;
* resolução;
* anotações;
* estrutura dos arquivos;
* homografias;
* parâmetros de câmera;

devem ser verificadas na fonte original antes de serem incluídas no texto.

Não inferir características do dataset apenas a partir de arquivos individuais.

---

## 11. Metodologia

A seção de metodologia deve diferenciar claramente:

### Problema

O que o sistema pretende resolver.

### Dados

Quais dados são utilizados.

### Métodos

Quais técnicas existem na literatura e quais serão utilizadas.

### Implementação

Como os métodos foram implementados.

### Avaliação

Como os resultados serão medidos.

Não confundir revisão bibliográfica com metodologia experimental.

---

## 12. Estrutura conceitual do sistema

A documentação deve manter coerência com o pipeline conceitual:

```text
Vídeo
  ↓
Detecção de jogadores
  ↓
Rastreamento
  ↓
Identificação da posição do jogador
  ↓
Transformação imagem → campo
  ↓
Posição no campo
  ↓
Visualização / análise
```

Caso novas etapas sejam adicionadas ao sistema, atualizar a documentação correspondente.

---

## 13. Homografia

A homografia é um componente importante da metodologia.

O documento deve deixar clara a direção da transformação utilizada.

Por exemplo:

```text
coordenadas da imagem
        ↓
      H
        ↓
coordenadas do campo
```

ou, caso seja utilizada a transformação inversa:

```text
coordenadas do campo
        ↓
     H^{-1}
        ↓
coordenadas da imagem
```

Não utilizar expressões como "aplicar a homografia" sem especificar o significado da transformação quando isso puder gerar ambiguidade.

---

## 14. Figuras

Figuras devem ser armazenadas em diretório apropriado, preferencialmente:

```text
figures/
```

No texto, utilizar referências cruzadas:

```latex
Como mostrado na Figura~\ref{fig:pipeline}, ...
```

e definir o identificador:

```latex
\label{fig:pipeline}
```

Não referenciar números de figuras manualmente.

Evitar:

```text
Como mostrado na Figura 3...
```

Preferir:

```latex
Como mostrado na Figura~\ref{fig:pipeline}...
```

---

## 15. Tabelas

Tabelas também devem utilizar referências cruzadas.

Exemplo:

```latex
Tabela~\ref{tab:resultados}
```

Não escrever números de tabelas manualmente.

Resultados experimentais devem possuir unidades e métricas claramente identificadas.

---

## 16. Equações

Equações importantes devem utilizar ambientes matemáticos apropriados e, quando forem referenciadas no texto, possuir `\label`.

Exemplo:

```latex
\begin{equation}
...
\label{eq:homografia}
\end{equation}
```

Referenciar utilizando:

```latex
\eqref{eq:homografia}
```

Não numerar equações manualmente.

---

## 17. Referências bibliográficas

As referências devem permanecer centralizadas no arquivo `.bib` utilizado pelo projeto.

Não inserir referências bibliográficas diretamente no texto.

Exemplo:

```latex
\cite{soccertrackv2}
```

A entrada correspondente deve estar no arquivo `.bib`.

Utilizar chaves de referência consistentes e legíveis.

Exemplo:

```bibtex
@article{soccertrackv2,
    ...
}
```

Não criar múltiplas entradas para o mesmo artigo.

---

## 18. Código

Trechos de código devem ser incluídos somente quando contribuírem para a explicação metodológica.

O artigo não deve se transformar em documentação completa do código-fonte.

Quando necessário, utilizar ambientes apropriados para código e indicar a linguagem.

---

## 19. Resultados

A seção de resultados deve apresentar dados obtidos experimentalmente.

Não inventar:

* métricas;
* valores;
* gráficos;
* comparações;
* número de detecções;
* desempenho;
* precisão;
* resultados de experimentos.

Se um resultado ainda não foi obtido, utilizar uma formulação indicando que o experimento ainda será realizado.

---

## 20. Discussão

A discussão deve separar claramente:

1. resultado observado;
2. interpretação;
3. possíveis causas;
4. limitações;
5. comparação com trabalhos anteriores.

Não apresentar uma hipótese como se fosse um resultado experimental confirmado.

---

## 21. Alterações no documento

Antes de modificar uma seção:

1. ler a seção completa;
2. verificar as referências utilizadas;
3. verificar as referências cruzadas;
4. verificar dependências com outras seções;
5. preservar a estrutura existente.

Ao modificar uma seção, evitar alterações não relacionadas em outras partes do documento.

---

## 22. Consistência entre código e artigo

O documento deve representar fielmente o sistema implementado.

Se o código utiliza uma técnica diferente daquela descrita no artigo, a documentação deve ser atualizada.

Da mesma forma, uma técnica descrita como parte da metodologia não deve ser apresentada como implementada se ainda não tiver sido desenvolvida.

Quando uma técnica for apenas uma possibilidade futura, identificá-la explicitamente como trabalho futuro ou alternativa a ser investigada.

---

## 23. Agentes de IA

Ao trabalhar neste repositório, o agente deve:

1. ler os arquivos relevantes antes de modificá-los;
2. preservar a estrutura existente;
3. não inventar referências;
4. não inventar resultados experimentais;
5. não inventar características do dataset;
6. manter consistência terminológica;
7. utilizar referências cruzadas do LaTeX;
8. utilizar citações bibliográficas adequadas;
9. verificar se novos comandos LaTeX são suportados pelo preâmbulo;
10. evitar alterações desnecessárias;
11. manter o texto academicamente objetivo;
12. verificar a compilação após alterações relevantes.

---

## 24. Regra para conteúdo científico

Quando uma afirmação depender de literatura científica, utilizar uma fonte verificável.

Quando houver dúvida entre:

* conhecimento geral;
* informação específica de um artigo;
* informação específica do dataset;
* resultado experimental;

não tratar essas categorias como equivalentes.

O texto deve deixar claro de onde cada informação provém.

---

## 25. Regra para resultados

**Resultados não podem ser inventados.**

Um agente pode:

* propor um experimento;
* criar a estrutura da tabela;
* criar a estrutura da seção;
* sugerir métricas;
* preparar gráficos que serão preenchidos posteriormente.

Um agente não pode preencher resultados com valores hipotéticos sem marcá-los explicitamente como exemplos.

---

## 26. Regra principal

Este repositório representa um trabalho acadêmico.

Ao realizar qualquer alteração, priorizar:

```text
correção científica
        ↓
clareza
        ↓
rastreabilidade das fontes
        ↓
reprodutibilidade
        ↓
consistência do documento
```

O objetivo não é apenas produzir um PDF visualmente correto, mas manter um documento que descreva de maneira fiel, verificável e academicamente adequada o sistema desenvolvido.
