# PHP Dynamic gifs countdown
Dynamic countdown gifs project
###### GIF DINÂMICO

Esse projeto de Contador GIF dinâmico não funciona como um GIF comum, toda vez que ele é carregado, é exibido a contagem regressiva absoluta, ao invés de reiniciar. 
Ou seja, se for definido que o fim será daqui 10 minutos, toda vez que eu carrega-lo ele me mostrará o tempo restante até se esgotar.
Para para possibilitar essa funcionalidade utilizei PHP e algumas bibliotecas como `GIFEncoder.class.php`

###### O FLUXO FUNCIONA ASSIM:

![Current Flow](https://raw.githubusercontent.com/lucasjordaom/dynamic-gifs-countdown/master/assets/current_flow.png)

1) *Requisição*
Primeiro é feito a requisição digitando o link no navegador, que a principio parece chamar um arquivo com a extensão .gif
`example.com/countdown/8bhw.gif`
2) *RewriteEngine*
Com o .htacess é feito uma reescrita interna, com auxilio de um regex.
Convertendo:
`<hash>.gif` para: `gif.php?id=<hash>`
Passando o hash via GET sem mudar a requisição original.
3) *Manda o hash pro banco*
O PHP captura o `$_GET` e consulta no banco o valor do Hash.
4) *Banco retorna os dados*
É retornado os dados necessários para criar o GIF como
- Cores
- Imagem de fundo
- Fonte
- Tamanho da fonte
- Tempo limite do contador
5) *Renderização*
O PHP junta os dados do banco e cria o GIF dinâmico.

###### O PROBLEMA
Hoje, ao fazer a requisição o resultado retorna um GIF bem pesado (1,5M aprox.) e isso impossibilita o uso em um e-mail Mkt por exemplo, se alguém souber de alguma API ou algum modo de diminuir esse peso total agradeço desde já !!


