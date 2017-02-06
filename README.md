# Codigo Barras i25 para Boleto PHP

Criação de código de barras, para suprir temporariamente o problema do Chrome em imprimir os boletos do [BoletoPHP](https://github.com/CobreGratis/boletophp)


## Problema

Foi reportado uma issue no projeto informando que o Chrome estava com problemas na impressão do código de barras

https://github.com/CobreGratis/boletophp/issues/103

Usuários levantaram que ao gerar o pdf e abrindo em outro lugar antes de imprimir, tudo ocorre bem, então ficou claro que era um problema no visualizador de PDF do Chrome

## Solução

A solução encontrada, pra se resolver rapidamente, foi criar um action (como utilizamos Zend) onde ela gera o código de barras.

Usando a função do [Aziz Vicentini](https://www.scriptbrasil.com.br/download/codigo/6491/), passo o código por GET, e é gerada a imagem


## Modificações BoletoPHP

Todo arquivo de layout do projeto BoletoPHP, possui uma chamada à função fbarcode(CODIGO). Essa função foi substituida pela imagem, algo assim

```php
	//fbarcode($dadosboleto["codigo_barras"]);
	echo "<img src=\"boleto_barcode.php?codigo=" . $dadosboleto["codigo_barras"] . "\">";
```
