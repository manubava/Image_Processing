# Image_Processing


## Introdução

O desafio proposto pela empresa Tarken envolve a análise de uma imagem para:
- Contar o número de estrelas e meteoros.
- Determinar quantos meteoros caíram na água.
- Encontrar a fase escondida.


## Ambiente de Desenvolvimento

O desenvolvimento e a execução do código foram realizados no Google Colab, utilizando:
- **Python** na versão 3.10.12.
- Biblioteca **Pillow (PIL)** para manipulação de imagens.

## Pixels: A Unidade Básica da Imagem

Os pixels ("picture elements") são os elementos básicos de uma imagem digital. Cada pixel representa uma pequena área da imagem e contém informações sobre cor e intensidade luminosa. Em imagens coloridas, um pixel geralmente é composto por três canais de cor: vermelho, verde e azul (RGB). 

Uma imagem digital é representada por uma matriz de pixels, onde cada pixel tem uma posição única identificada por suas coordenadas (x, y):
- **x**: posição horizontal (coluna).
- **y**: posição vertical (linha).

## Pontos Conectados

A abordagem foi desenvolvida para verificar se uma estrela ou meteoro é composto por mais de um pixel, contabilizando esse agrupamento como uma entidade única. O algoritmo examina todos os pixels de uma região conectada antes de passar para as regiões vizinhas, garantindo que cada estrela ou meteoro seja contado como um único elemento.

## Contagem de Estrelas e Meteoros

O algoritmo percorre cada pixel da imagem, utilizando um algoritmo de região conectada para identificar e contabilizar pixels brancos (estrelas) ou vermelhos (meteoros) como pertencentes a uma única entidade.

## Contagem de Meteoros na Água

Para detectar meteoros caindo na água, o código verifica se há pixels de cor azul abaixo da trajetória do meteoro. Se encontrar um pixel azul, significa que o meteoro está caindo na água.

## Metodologia e Aplicação

O código foi planejado em etapas, cada uma com uma função específica:

1. **Carregar a imagem:** A função "carregar_imagem" carrega a imagem especificada pelo caminho fornecido e retorna os pixels, largura e altura.
2. **Contar estrelas e meteoros:** As funções "contar_estrelas" e "contar_meteoros" percorrem cada pixel da imagem, verificando as cores e chamando "regiao_conectada" para verificar regiões conectadas.
3. **Verificar se o meteoro está na água:** A função "meteoro_na_agua" verifica se um meteoro está caindo na água percorrendo os pixels abaixo do meteoro.
4. **Verificar regiões conectadas:** A função "regiao_conectada" verifica se um pixel faz parte de uma região conectada de pixels com a mesma cor.
5. **Função principal:** A função "contar_estrelas_e_meteoros" chama as funções anteriores para carregar a imagem, contar estrelas e meteoros, e retornar os resultados.

---
