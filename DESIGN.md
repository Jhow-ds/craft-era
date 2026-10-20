# DESIGN — Craft Era

Sistema visual da bancada. Este arquivo descreve o que já está construído em
`index.html`, não uma intenção. Se o código divergir daqui, o código é a
verdade e este arquivo precisa ser corrigido.

Direção aprovada: **Bancada de Engrenagens** — a mesa de um mecânico, uma chapa
de inspeção com graduação, e cada invenção representada pelo artefato material
que ela realmente foi. Não há cartões flutuantes, não há gradientes de vidro,
não há ícones genéricos de biblioteca: todo desenho de item é SVG autoral.

## 1. O mundo

- **A superfície é uma chapa.** Fundo escuro, graduação de 40 × 40 em trama de
  1 px, marcas de canto e um datum central. A trama não é decoração: é a régua
  da bancada (e é a única superfície do produto onde grade é legítima).
- **A era é pátina.** Cada invenção carrega a cor da sua era na faixa superior
  da peça, no rótulo do registro e no acento da página. A cor acompanha a
  última invenção descoberta.
- **O vazio é layout.** A bancada é grande de propósito; peças pequenas
  espalhadas nela leem como componentes sobre uma mesa, não como uma grade de
  cartões. Nunca preencher o vazio com enfeite — preencher com informação
  (marcos, peças, receita).
- **Um artefato por invenção.** Roda é um aro com raios, não um ícone de
  engrenagem. Prensa é uma estrutura com fuso. O desenho precisa ser
  reconhecível como o objeto físico.
- **Matéria tem cor; abstração tem linha.** Sólidos de corpo único (madeira,
  pedra, vidro, metal, água, fogo) recebem uma pátina de material;
  mecanismo fino (prensa, tear), diagrama (fluxograma) e abstração (internet,
  código, rede neural) continuam em linha pura — a pátina não sobrevive a
  6 px de traço. São 64 dos 104 itens. A pátina é dessaturada por construção:
  a era segue sendo a única cor viva da tela.

## 2. Cores

```
--fundo       #14120f   plano da página
--chapa       #1a1714   superfície da bancada
--chapa-alta  #211d19   peça, linha de tentativa
--chapa-fundo #151210   rodapé de registro
--trilho      #322c26   divisórias de 1 px
--trilho-2    #3d362e   bordas de controle
--tinta       #ece6da   texto principal  (14,4:1 sobre a chapa)
--tinta-2     #b3a999   texto corrido     (7,7:1)
--tinta-3     #8d8478   rótulos mono     (4,9:1 — piso do sistema)
--grava       rgba(216,203,180,.05)  graduação da chapa
```

Paleta de eras (`cor` = traço/gráfico, `txt` = texto e fundo de chip):

| Era | cor | txt |
|---|---|---|
| I · Terra | `#a2543a` | `#e08a5f` |
| II · Bronze | `#3f8578` | `#63bdae` |
| III · Ferro | `#6d7684` | `#9fa9b6` |
| IV · Vapor | `#b06a3b` | `#e09a5c` |
| V · Elétrica | `#c9a227` | `#e6c55c` |
| VI · Digital | `#3fa9c4` | `#6fcbe0` |
| VII · Espectro | `#d94f8c` | `#f07bb0` |

**Regra:** texto sobre cor de era usa sempre o tom `txt` como fundo com texto
`#17130f`. O tom escuro não serve de fundo para texto (terra cai a 3,4:1). O
tom escuro só aparece em elementos gráficos: faixa da peça, quadrado de marco,
ponto de cadeia, faísca.

Pátina de material (`--p3`, só em sólidos de corpo único):

| Família | hex | itens |
|---|---|---|
| madeira | `#6f4a2e` | madeira, tábua |
| fibra | `#7a6f58` | fibra, corda, papel, tecido, cartão, livro, códice |
| pedra | `#5f5c55` | pedra, areia, cal, carvão, mineral |
| água | `#3f5e6a` | água |
| vidro | `#5c767c` | vidro, cristal, lente, lâmpada, válvula, tela |
| metal | `#59616a` | barra, cobre, estanho, bronze, ferro, tipo, caldeira, pistão, condutor |
| fogo | `#843f23` | fogo, forno |
| óleo | `#6a5426` | óleo, pilha, bateria |
| tinta | `#3f4f6a` | tinta |
| digital | `#4a5a66` | silício, germânio, transistor, circuito, memória, microprocessador, monitor, celular, navegador, corpus, modelo |

A pátina entra como terceiro slot do `traco()` e sai da mesma silhueta que
o traço primário. No PDF ela vira tint sobre papel — `mistura(cor, branco,
.82)` —, nunca bloco escuro.

## 3. Tipografia

```
--display  "Big Shoulders Display" 600/800   título, nome de invenção
--texto    "Archivo" 400/500/600             leitura corrida
--medida   "Fragment Mono"                   medidas, rótulos, contadores
```

| Uso | Fonte | Tamanho | Caixa |
|---|---|---|---|
| Marca | display 800 | 33 px | original |
| Nome de invenção (registro, revelação) | display 600 | 25 / 40 px | original |
| Corpo | Archivo 400 | 12,5–14 px / 1,6–1,68 | frase |
| Rótulo da peça | display 600 | 13 px | CAIXA ALTA, `ls .02em`, acima do assento |
| Botão, era, contador | mono | 11 px | CAIXA ALTA |
| Rótulo de bloco | mono | 10 px | CAIXA ALTA, `ls .15em` |
| Medida da peça | mono | 8,5 px | CAIXA ALTA |

Piso: **11 px** para texto funcional (botão, nav, contador). 8,5–10 px só em
rótulo decorativo não interativo.

## 4. Espaço e forma

- Grade da página: `76px / 1fr / 196px` no desktop, com a bancada à esquerda,
  a gaveta de 320 px à direita e o rodapé dividido entre fita e nota. Abaixo de
  980 px a bancada ocupa a largura toda, a gaveta vira faixa sob ela e fita e
  nota continuam lado a lado no rodapé; abaixo de 720 px tudo empilha.
- Peça: 132 × ~169 px no total — rótulo acima, assento de 132 × 132 px (raio
  9 px, borda 1 px `--trilho`, faixa de 4 px na aresta de cima), medida abaixo.
- Raio de painel: 14 px.
- Respiro padrão: 8 / 14 / 18 / 24 / 30 px.
- A chapa inteira é área útil: a gaveta saiu do rodapé e virou coluna, então a
  bancada não desconta altura de bandeja nenhuma.

## 5. Componentes

- **Peça** — gramática de chapa: rótulo em condensada industrial ACIMA do
  assento, assento com faixa da era e SVG de 66 px, medida em monoespaçada
  ABAIXO (ano real em caixa alta ou `CONSTRUÇÃO DIDÁTICA`). O ponto cinza no
  canto superior direito marca degrau didático; a corrente de nós no canto
  esquerdo conta as etapas da montagem (elos de 1 px ligando os nós).
  Arrastável; hover acende a borda do assento (a ficha é só da gaveta); alvo
  recebe contorno tracejado da cor da era; falha sacode (`nega`). Clique com o
  botão direito (ou `Delete`) remove a peça da bancada sem perdê-la na gaveta.
- **Gaveta** — coluna à direita da bancada, com rolagem vertical e uma seção
  por era (cabeçalho fixo com cor, nome e `descobertos/total`). Lista tudo que
  já foi descoberto como linha de ícone, nome e ano. Clique traz uma cópia;
  arrastar uma peça até aqui a devolve. É o que impede a partida de travar por
  falta de material e o que evita a tira horizontal de 104 peças.
- **Dica** — ficha de 312 px que abre no hover ou no foco de uma peça da
  gaveta; a bancada não abre ficha. Traz era e selo de marco, nome, data e
  autor, `COMO FOI CRIADO` (a receita que a produz), `O QUE É` (primeira frase
  do registro ou a marca de degrau didático) e `DESBLOQUEIA` (tudo que a peça
  destrava). Fica no lado com mais espaço e desaparece no arraste e na rolagem.
- **Fita** — metade esquerda do rodapé, com a receita ativa. Duas etapas
  mostram `+` e a legenda `ORDEM LIVRE`; três ou quatro mostram `01 → 02 → …`
  e `A ORDEM IMPORTA`. A ordem exibida é a histórica, não a do gesto.
- **Nota** — metade direita do rodapé, ao lado da fita: tentativa atual e
  registro da última descoberta (nome, ano, autor, texto, selos, o que
  destrava). Sem tentativa e sem registro, o painel mostra a instrução de
  estreia; com registro, a leitura histórica ocupa o espaço sozinha.
- **Código** — painel de 460 px com todas as eras; item não descoberto aparece
  em silhueta, com nome mascarado. É referência, não receituário.
- **Revelação** — caixa de 560 px, faixa da cor da era no topo, título grande,
  e sob ele a linha de metadados (era, selo de invenção central, data, autor),
  o texto e duas ações. Sem tarja acima do título: o título abre a caixa por si
  (tarja acima de título é banida pelo craft floor). Abre só para as dez
  invenções centrais, e o aviso pendente da bancada é dispensado no mesmo
  instante, para não contradizer a descoberta.
- **Aviso** — faixa de status de 2,1 s para falhas e limites.

## 6. Movimento

- Chegada de peça: `chegar` 500 ms, escala .82 → 1.
- Recusa: `negar` 340 ms, deslocamento de ±7 px.
- Aproximação: o alvo pulsa um campo de 1 px na cor da era (`campo`, 1,15 s,
  loop) e a linha de união ganha 2 px e brilho (`fluxo`, 0,9 s). Enquanto dura
  o arraste, o assento levantado recebe um halo da era.
- Síntese: núcleo, três ondas e o assento novo aceso (`forja` e `sintese`,
  620–780 ms). Só quando a receita fecha, no ponto exato onde os dois
  componentes se encontraram.
- Descoberta: o fogo tem três quadros (160 ms cada, 980 ms no total). A peça
  acende no instante em que nasce e assenta no quadro 1 — só na primeira vez
  que aquele item é descoberto. Na bancada, na gaveta, no códice e no PDF o
  desenho é estático.
- Tudo acima é desligado por `prefers-reduced-motion`.

## 7. Acessibilidade

- Contraste medido: principal 14,4:1 · secundário 7,7:1 · rótulos 4,9:1 ·
  chip de era 7,0–11,0:1.
- Cada peça é `role="button"`, focável, com `aria-label` que inclui ano ou
  marcação didática, o número de etapas e a instrução de remoção.
- Teclado: setas movem a peça, Enter/Space levanta e engata, `Delete` remove
  a peça da bancada, Escape fecha revelação e código. A gaveta é uma lista de
  botões agrupada por era; hover e foco abrem a mesma ficha, e a revelação dos
  grupos respeita a ordem das eras no DOM.
- Regiões `aria-live` para a fala do leitor e para o aviso.
- Touch: `touch-action:none` nas peças; alvos de 132 px; na gaveta a linha
  inteira é o alvo, não só o ícone.

## 8. O que este sistema recusa

- Grade de cartões alinhados como layout principal.
- Vidro fosco, brilho, gradiente decorativo, borda arco-íris.
- Emoji como arte de item.
- Pátina em abstração (internet, código, rede neural) ou em mecanismo fino:
  a cor é matéria, não paleta.
- Ordem de receita dependente de qual peça foi arrastada sobre qual.
- Cor de era usada como fundo de texto sem checar contraste.
- Glifo de fonte no papel de ícone: marcas são desenhadas em CSS (círculo,
  losango, corrente de nós), nunca `★ ● ○ ■`. O `+` da fita é operador de
  receita, não ícone.
- Tarja ou rótulo acima de um título (`craft floor`).
