# Image_Processing
Análise de uma imagem digital com o objetivo de contar o número de estrelas e meteoros presentes, identificar quantos meteoros caíiriam na água 



  Introdução
O desafio a seguir foi proposto pela empresa Tarken e envolve a análise de uma imagem. O objetivo era contar o número de estrelas e meteoros, quantos meteoros caíram na água e encontrar a fase escondida. Para isso, um dos aspectos fundamentais na análise de imagens é a compreensão dos pixels que compõem a imagem e como eles podem ser analisados para extrair informações úteis.


Ambiente de desenvolvimento
O desenvolvimento e a execução do código foram realizados no Google Colab, utilizando Python na versão 3.10.12. E a biblioteca utilizada para a manipulação de imagens foi a Pillow (PIL), instalada e importada no ambiente Colab. 


Pixels: A Unidade Básica da Imagem

Os pixels, abreviação de "picture elements", são os elementos básicos que compõem uma imagem digital. Cada pixel representa uma pequena área da imagem e contém informações sobre a cor e a intensidade luminosa dessa área, sendo definidos como um conjunto de elementos discretos e de tamanhos finitos. Em imagens coloridas, um pixel geralmente é composto por três canais de cor: vermelho, verde e azul (RGB). Em algumas imagens, um quarto canal alfa pode ser adicionado para representar transparência.
Sabe-se que uma imagem digital é representada por uma matriz como uma grade de pixels. Sendo que cada pixel tem uma posição única identificada por suas coordenadas (x, y):
x representa a posição horizontal (a coluna) do pixel.
y representa a posição vertical (a linha) do pixel.
Por exemplo, as coordenadas (0, 0) correspondem ao pixel no canto superior esquerdo da imagem. À medida que você move para a direita, o valor de x aumenta, e à medida que você move para baixo, o valor de y aumenta.Ao atribuir x, y = 10, 10, estamos simplesmente escolhendo um pixel localizado na coluna 10 e linha 10 da imagem. 
             
Neste contexto, a área de processamento de imagens se dedica à manipulação desses pixels com os seguintes objetivos: aprimoramento da imagem, remoção de elementos indesejados e extração de informações.


Representação
Internamente, os pixels são representados por valores numéricos que indicam a intensidade de cada canal de cor. Por exemplo, um pixel branco pode ser representado por (255, 255, 255), indicando intensidades máximas de vermelho, verde e azul. E um pixel preto seria representado por (0, 0, 0), indicando intensidades mínimas em todos os canais. A imagem a seguir representa o modelo RGB:



Pontos conectados

Esta abordagem foi desenvolvida para verificar se uma estrela ou meteoro é composto por mais de um pixel e contabilizar esse agrupamento como uma entidade única, mesmo que sejam formados por vários pixels adjacentes.
Considerar a vizinhança em uma imagem digital refere-se à maneira como os pixels são considerados adjacentes uns aos outros. Sendo assim, o algoritmo examinará todos os pixels de uma região conectada antes de passar para as regiões vizinhas. Essa abordagem assegura que cada estrela ou meteoro, mesmo que formado por vários pixels, seja contado como um único elemento.


Contagem de Estrelas e meteoros

Para contar as estrelas e meteoros na imagem, o algoritmo percorre cada pixel da imagem. Sempre que encontrar um pixel branco (representando uma estrela) ou vermelho(representando uma meteoro), utiliza um algoritmo de região conectada para identificar todos os pixels adjacentes a ele para serem contabilizados como pertencentes a um elemento. Essa técnica garante que estrelas e meteoros compostos por múltiplos pixels sejam contadas como uma única entidade.



Contagem de Meteoros na Água

Para detectar uma possível queda de meteoros na água, o código verifica se há pixels de cor azul nos pixels da coluna que estão abaixo da trajetória do meteoro. Isso é feito percorrendo os pixels abaixo da posição do meteoro e verificando se algum deles corresponde à cor da água.
Se for encontrado um pixel azul, significa que o meteoro está caindo na água, e a função retorna de verdade. Caso contrário, retorna falso.




Metodologia e Aplicação

O código foi planejado em etapas, cada uma com uma função específica:

1. Carregar a imagem: A função “carregar_imagem” carrega a imagem especificada pelo caminho fornecido e retorna os pixels da imagem, bem como sua largura e altura.

2. Contagem: As funções “contar_estrelas” e “contar_meteoros” percorrem cada pixel da imagem e verifica se a cor do pixel é branca (255,255,255) ou vermelha(255,0,0). Se for, ela chama a função “regiao_conectada” para verificar se o pixel faz parte de uma região conectada de pixels brancos. Se for, a contagem de estrelas é incrementada.

3. Verificar se o meteoro está na água: A função “meteoro_na_agua” verifica se um meteoro está caindo na água. Ela percorre os pixels abaixo do meteoro até encontrar um pixel preto (0, 0, 0) ou um pixel azul (0, 0, 255). Se encontrar um pixel azul, significa que o meteoro está caindo na água.

4. Verificar regiões conectadas: A função “regiao_conectada” verifica se um pixel faz parte de uma região conectada de pixels com a mesma cor. 

5. Função principal: A função “contar_estrelas_e_meteoros” chama as funções anteriores para carregar a imagem, contar as estrelas e meteoros, e retornar os resultados.
