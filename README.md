# Scripts-Tabela-Portal

Este script foi criado com o intuito de obter os dados gerais sobre a COVID no Brasil. Os mesmos estarão visíveis em cards na página inicial do portal [Covid Data Analytics](http://covid.dcc.ufmg.br/).
A parte principal do código se encontra abaixo, onde é feita uma simples requisição a um repositório do github que atualiza os dados da COVID periódicamente. 
*(O código a seguir esta dentro de um html e pode ser visto na íntegra em: códigos -> cards.html")*
```
var request = new XMLHttpRequest(); 
    request.open("GET","https://raw.githubusercontent.com/wcota/covid19br/master/cases-brazil-total.csv"); 
    request.addEventListener('load', function(event) { 
       if (request.status >= 200 && request.status < 300) { 
          //Função chamada caso a "request" retorne um valor válido.
          successFunction(request.responseText)
       } else { 
          console.warn(request.statusText, request.responseText); 
       } 
    }); 
    request.send();
```
*Fonte dos dados: [Wesley Cota](https://github.com/wcota/covid19br)*

A forma na qual os dados são retornados pode ser vista na imagem abaixo.
Estas são as três primeiras linhas dos resultados obtidos em uma execução realizada no dia 25/11/2020.
*(A tebela completa e **atualizada** pode ser vista em: códigos -> tabela-original.html)*

| country | state | totalCases | totalCasesMS | notConfirmedByMS | deaths | deathsMS | URL                             | deaths_per_100k_inhabitants | totalCases_per_100k_inhabitants | deaths_by_totalCases | recovered | suspects | tests    | tests_per_100k_inhabitants | date       | newCases | newDeaths |
|---------|-------|------------|--------------|------------------|--------|----------|---------------------------------|-----------------------------|---------------------------------|----------------------|-----------|----------|----------|----------------------------|------------|----------|-----------|
| Brazil  | TOTAL | 6124152    | 6118708      | 5444             | 170240 | 170115   | https://covid.saude.gov.br/     | 80.39453                    | 2892.08377                      | 0.02780              | 5509645   |          | 22711485 | 10725.32445                | 2020-11-24 | 31933    | 619       |
| Brazil  | AC    | 35053      | 35053        | 0                | 715    | 715      | http://saude.acre.gov.br/       | 81.07173                    | 3974.55595                      | 0.02040              | 30179     |          | 97038    | 11002.85168                | 2020-11-24 | 204      | 1         |
| Brazil  | AL    | 93708      | 93708        | 0                | 2324   | 2324     | http://cidadao.saude.al.gov.br/ | 69.63594                    | 2807.85064                      | 0.02480              | 90475     |          | 208002   | 6232.53670                 | 2020-11-24 | 139      | 3         |


A partir daí, ocorreu apenas uma filtragem simples dos dados que aparecem no portal.


# Vizualizando os cards localmente (Executando o script em ambiente local)
O procedimento para executar o script em sua máquina é muito simples:
1. Certifique-se de ter os seguintes arquivos baixados em seu computador: **cards.html e styles.css**.
2. Crie um diretório e coloque os dois arquivos dentro.

![](https://github.com/thiagosantos0/teste55/blob/main/imagens/Captura%20de%20tela%20de%202020-11-25%2019-21-24.png)

Está tudo pronto, basta abrir o arquivo html em um navegador. Este html tem um código javascript que realiza a chamada dos dados sempre que a página sofre algum tipo de atualização, deste modo não há a necessidade de executá-lo manualmente.
*(A aparência dos cards na imagem abaixo é referente ao dia 25/11/2020)*

![](https://github.com/thiagosantos0/teste55/blob/main/imagens/im2.png)

