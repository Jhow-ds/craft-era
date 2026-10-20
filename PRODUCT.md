# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Static HTML/CSS/JS, arquivo único (`index.html`). Escolha do usuário, confirmada na entrevista inicial. Sem build, sem servidor, sem dependências: abrir com duplo clique precisa funcionar.

## Users

Uso educacional. Professor, aluno ou entusiasta que abre o jogo como exercício de aula ou de estudo pessoal. Espera conteúdo datado e atribuído com exatidão — a autoridade histórica é parte do produto, não um ornamento.

## Product Purpose

Um jogo de combinação no formato Infinity Craft em que a árvore de receitas é uma genealogia das invenções da história. O jogador arrasta itens, aproxima dois e descobre se a combinação corresponde a uma invenção real. Do material bruto até a inteligência artificial generativa, cada marco da história humana aparece como resultado de um encadeamento de pré-requisitos.

Sucesso significa que o jogador chega à IA generativa e entende, no caminho, que nenhuma invenção é um gênio isolado: a roda se perdeu com a destruição da Biblioteca de Alexandria, a tear de Jacquard precedeu o computador em dois séculos, e a imprensa de Gutenberg exigiu o papel e a tinta que a China e o mundo islâmico tinham desenvolvido antes.

## Positioning

O diferencial não é combinar coisas, é a **genealogia**. Um jogo de combinação comum aceita qualquer par de objetos. Aqui a árvore impõe ordem e dependência: você não pode fabricar um smartphone sem antes ter resolvido o computador pessoal, a internet, a tela de LCD e a bateria de íon-lítio. A ordem dos ingredientes importa, e essa ordem é a ordem real em que a história aconteceu.

Padrão de fidelidade **misto, declarado**: os marcos de invenção são reais, datados e atribuídos a quem os fez. Os materiais e etapas intermediárias são construções didáticas do próprio jogo e são rotulados como tais na interface. O jogo nunca apresenta uma simplificação como se fosse fato histórico.

## Operating Context

- Sessão de aula ou estudo individual, em desktop ou tablet, em contexto de navegador.
- O jogador precisa que a passagem do gesto (combinar dois itens) para o conhecimento (por que isso se inventou, e quando) seja imediata e inequívoca.
- Materiais e arte são desenhados em SVG pelo próprio projeto — não há dependência de assets externos, imagens de terceiros ou fontes hospedadas.

## Capabilities and Constraints

- Mecânica: arrastar itens em um espaço livre; a proximidade de dois itens dispara a tentativa de receita. Receitas de 2 ingredientes são livres de ordem; receitas de 3–4 exigem a ordem histórica de montagem. A coluna de peças fica à direita da bancada, separada por era, com a ficha de cada item no hover — só na coluna; na bancada o hover não abre ficha. Clique traz uma cópia, arrastar até a coluna devolve, e o botão direito sobre uma peça da bancada a remove.
- Receitas de 2 a 4 ingredientes, profundidade suficiente para que a IA generativa exija a cadeia completa.
- Cada invenção descoberta abre um registro histórico no rodapé, ao lado da fita de receita: ano, responsável, e o que aquela invenção destravou.
- Progressão organizada por eras, cada era com identidade cromática própria.
- Idioma: português do Brasil.
- Sem build step. A interface precisa funcionar a partir de `file://`.
- **Fato deliberadamente não decidido:** comportamento de áudio. Nada de som foi especificado; qualquer adição futura é decisão do usuário, não um resíduo de implementação.

## Brand Commitments

- Nome: *Craft Era*.
- Restrição visual vinculante, oferecida pelo usuário na entrevista: **progressão por eras, com cor própria para cada era**. A paleta não é decoração: cada cor codifica o período histórico do item, e essa codificação é legível por si só.
- Regra de honestidade material: conteúdo histórico é factual e verificável; conteúdo didático é identificado como tal.

## Evidence on Hand

Nenhum asset, imagem, fonte de dados ou material de marca pré-existente. Todos os SVGs são autorais e desenhados para este projeto.

O que **não** existe e não deve ser fabricado: depoimentos, estatísticas de usuários, registros de desempenho histórico, preços, licenças de terceiros ou qualquer número que o jogo não consiga sustentar com a própria árvore.

## Product Principles

1. **Acumulação, não gênio.** Toda invenção tem predecessores nomeados. A árvore é o argumento.
2. **O marco é real; o degrau é didático.** Cada item do jogo declara se é fato histórico ou construção didática, sem exceção e sem ambiguidade.
3. **O gesto ensina.** A combinação errada é tão parte da aprendizagem quanto a combinação certa.
4. **A era é a cor.** A identidade cromática carrega informação, não ornamento — por isso a única cor saturada da tela é a da era: a pátina de material é dessaturada por construção.
5. **Ensinar primeiro, estética segundo.** Se a aula exigir precisão histórica, ela vence a estética.

## Accessibility & Inclusion

Requisito de sala de aula: legibilidade em projetor e em tela pequena, navegação por teclado, e contraste que se sustente em brilho alto. Materiais de apoio para o uso educacional (lista de marcos, datas) são parte da entrega esperada.