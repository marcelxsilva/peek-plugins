# Como criar um plugin

Um plugin é um arquivo JSON que diz ao Peek três coisas: de onde ler, o que mostrar e quais botões oferecer. Você não precisa escrever esse arquivo à mão. O Peek monta tudo com você, com os dados de verdade na tela.

A especificação completa, chave por chave, está no [manifesto](https://peek.marcelxsilva.dev/manifesto).

&nbsp;

## De onde ele lê

O plugin lê de uma destas fontes:

- **Endereço**: uma API na internet ou uma máquina da sua rede, com os cabeçalhos e o token que ela pedir.
- **Programa**: um executável do seu Mac, como o `gh` ou o `kubectl`. A resposta pode ser JSON, texto, linhas, colunas ou pares de nome e valor.
- **Script**: AppleScript ou JavaScript for Automation, para falar com os apps do Mac.
- **Nada**: o plugin é um painel de botões, e cada botão traz a própria resposta.

Os tokens ficam nas Chaves do Mac, nunca no arquivo. Por isso um plugin pode ser compartilhado sem vazar nada.

&nbsp;

## O que ele mostra

**O ícone** fica na borda da tela. Dentro dele vai um símbolo, uma palavra curta ou uma imagem. Abaixo, um rótulo com um valor curto. Em volta, um arco de progresso, um número, uma cor de status ou um gráfico pequeno das últimas leituras. Quando algo muda, ele salta.

**O cartão** abre quando o cursor para no ícone. Ele é feito de blocos, empilhados na ordem que você quiser:

| Bloco | O que mostra |
| --- | --- |
| Destaque | Um número importante, a variação e a distância até a meta. |
| Tendência | Como um valor se moveu ao longo do tempo, em linha, área ou barras. |
| Mapa de calor | Intensidade por dia e hora, ou por dia do mês. |
| Barras ranqueadas | Itens ordenados do maior para o menor. |
| Etapas | Uma contagem por etapa, na ordem. Um clique filtra a lista. |
| Distribuição | Como os itens de uma lista se dividem entre grupos, em barra, funil ou lista. |
| Grade de status | Muitos itens de uma vez, cada um bem ou não. |
| Linha do tempo | O que aconteceu e o que vem, por data. |
| Tabela | Colunas de valores curtos, com imagem, status ou botão por linha. |
| Texto | Um parágrafo para ler, com um botão de copiar. |
| Lista | Linhas com título, status, imagem e link, em abas. |
| Botões | Um painel de botões, cada um rodando alguma coisa. |
| Propriedades | Pares de nome e valor, com botões ao lado de cada um. |
| Controles | Interruptores e níveis, direto no cartão. |

Quase todo bloco pode ocupar meia largura, e dois blocos de meia largura dividem a mesma linha.

Todo texto do cartão pode misturar palavras com campos da resposta. Um campo mostra o valor que veio naquela leitura, e um formato ajusta como ele aparece: arredondado, em percentual, como dinheiro, em tempo relativo, em tamanho de arquivo.

Um cartão feito com blocos:

<p align="center">
  <img src="assets/atividade.png" alt="O Peek na borda direita da tela, com o cartão Atividade aberto mostrando acessos por hora, commits por dia e chamados de hoje" width="640">
</p>

&nbsp;

## Os botões

Um botão pode ficar no topo do cartão, em cada linha de uma lista, num painel de botões, numa coluna de tabela, ao lado de uma propriedade ou por trás de um controle.

Ele chama um endereço, roda um programa ou um script, ou faz algo no Mac: copia um texto, abre um link ou um app, manda uma notificação, toca um som, roda um Atalho ou guarda um link em Ler mais tarde.

Antes de rodar, ele pode pedir confirmação ou perguntar um valor. Depois, mostra uma frase, a saída do programa, ou nada. Regras olham a resposta e decidem o resto: mudar a cor do botão, escrever uma linha, mostrar uma imagem, rodar outra chamada ou fazer o ícone saltar. Quando dá certo, o plugin lê de novo e mostra o estado novo.

&nbsp;

## Passo a passo

1. No Peek, abra **Configurações › Plugins** e clique em **Novo plugin**.
2. Em **Dados**, escolha a fonte e clique em **Verificar**. O Peek mostra o que veio.
3. Escolha um começo: uma lista, abas com listas, um número ou um botão. O Peek monta um rascunho já preenchido.
4. Em **Ícone**, escolha o que fica na borda da tela.
5. Em **Detalhes**, ajuste o cartão e adicione blocos. Todo campo tem um **+** para escolher um valor da resposta, e o cartão se atualiza na hora.
6. Em **Notificações**, diga quando o ícone deve chamar você.
7. Clique em **Criar plugin**. Ele vira um ícone na borda da tela.

Para levar o plugin para outro Mac ou mandar para alguém, use **Arquivo › Copiar** no editor e importe do outro lado em **Configurações › Plugins › Importar**.

&nbsp;

## Com a ajuda da IA

Prefere descrever em vez de montar? Na [página do manifesto](https://peek.marcelxsilva.dev/manifesto#ia), escreva o que o plugin deve fazer, copie o prompt e cole no seu modelo de IA. Ele devolve o arquivo pronto para importar.

&nbsp;

## Para se inspirar

Os [plugins deste repositório](plugins/) servem de ponto de partida. Instale um parecido com o que você quer pela [página de plugins](https://peek.marcelxsilva.dev/plugins) e ajuste no editor.

Quer ver o seu plugin aqui? Abra um pull request com o arquivo em `plugins/` e uma linha nova em `index.json`.
