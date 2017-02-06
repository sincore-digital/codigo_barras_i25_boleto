# Codigo Barras i25 Boleto

Criação de código de barras, para suprir temporariamente o problema do Chrome em imprimir os boletos do PHP-Boletos


## Problema

Foi reportado uma issue no projeto informando que o Chrome estava com problemas na impressão do código de barras

https://github.com/CobreGratis/boletophp/issues/103

Usuários levantaram que ao gerar o pdf e abrindo em outro lugar antes de imprimir, tudo ocorre bem, então ficou claro que era um problema no visualizador de PDF do Chrome

## Solução

A solução encontrada, pra se resolver rapidamente, foi criar um action (como utilizamos Zend) onde ela gera o código de barras.

Usando a função do Aziz Vicentini, passo o código por GET, e é gerada a imagem

# Modificações PHP_Boleto

Todo arquivo de layout do projeto PHP_Boleto, possui uma chamada à função fbarcode(CODIGO). Essa função foi substituida pela imagem, algo assim

echo "<img src=\"http://localhost/unimedandradina.com.br/public_html/sistema/boleto/barcode/codigo/" . $dadosboleto["codigo_barras"] . "\">";
