# Como criar um plugin

Um plugin é um arquivo JSON que diz ao Peek três coisas: de onde ler, o que mostrar e quais botões oferecer. Você não precisa escrever esse arquivo à mão. O Peek monta tudo com você, com os dados de verdade na tela.

&nbsp;

## De onde ele lê

O plugin lê de uma destas fontes:

- **Endereço**: uma API na internet ou uma máquina da sua rede, com os cabeçalhos e o token que ela pedir.
- **Programa**: um executável do seu Mac que devolve JSON.
- **Script**: AppleScript ou JavaScript for Automation, para falar com os apps do Mac.
- **Botões**: não lê nada. O plugin é um painel de botões, e cada botão traz a própria resposta.

Os tokens ficam nas Chaves do Mac, nunca no arquivo. Por isso um plugin pode ser compartilhado sem vazar nada.

&nbsp;

## O que ele mostra

O ícone na borda da tela mostra um valor curto, como uma contagem, um percentual ou um horário. Ele pode ter um arco de progresso e pode saltar quando algo muda.

O cartão, que abre quando o cursor para no ícone, é feito de **blocos**. Cada bloco desenha uma parte da resposta: um número em destaque, um gráfico, uma lista, uma tabela, uma grade de status, pares de nome e valor, interruptores, uma divisão por grupos. Você empilha os blocos na ordem que quiser, e dois blocos pequenos podem ficar lado a lado.

Todo texto do cartão pode misturar palavras com campos da resposta. Um campo mostra o valor que veio naquela leitura, e um formato ajusta como ele aparece: arredondado, em percentual, em tempo relativo, em tamanho de arquivo.

Um cartão feito com blocos:

<p align="center">
  <img src="assets/atividade.png" alt="O Peek na borda direita da tela, com o cartão Atividade aberto mostrando acessos por hora, commits por dia e chamados de hoje" width="640">
</p>

&nbsp;

## Os botões

Um botão pode ficar no topo do cartão, em cada linha de uma lista ou num painel próprio. Ele chama um endereço, roda um programa, copia um texto ou abre um link. Pode pedir confirmação antes, perguntar um valor e mostrar o que voltou. Depois, o plugin pode se ler de novo para mostrar o estado novo.

&nbsp;

## Passo a passo

1. No Peek, abra **Configurações › Plugins** e clique em **Novo plugin**.
2. Escolha a fonte e leia uma vez. O Peek mostra o que veio.
3. Escolha um formato para começar: um número, uma lista, várias listas ou lista com botão.
4. Arraste os campos da resposta para o cartão. O cartão se atualiza na hora, com os dados de verdade.
5. Salve. O plugin vira um ícone na borda da tela.

Para levar o plugin para outro Mac ou mandar para alguém, exporte o arquivo e importe do outro lado em **Configurações › Plugins › Importar**.

&nbsp;

## Com a ajuda da IA

Prefere descrever em vez de montar? Na [página do manifesto](https://peek.marcelxsilva.dev/manifesto#ia), escreva o que o plugin deve fazer, copie o prompt e cole no seu modelo de IA. Ele devolve o arquivo pronto para importar.

&nbsp;

## Para se inspirar

Os [plugins deste repositório](plugins/) servem de ponto de partida. Baixe um parecido com o que você quer, importe no Peek e ajuste.

Quer ver o seu plugin aqui? Abra um pull request com o arquivo em `plugins/` e uma linha nova em `index.json`.
