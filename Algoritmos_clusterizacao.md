## SKATER

Biblioteca: **Pygeoda**

Baseia-se na poda de árvores criadar por grafos, conde todos os pontos são conectados sem nós isolados.

Constói uma árvore geradora mínima, onde as conexões entre vizinhos recebem pesos  com base na distância/dissimilaridade.

O objetivo é reduzir a SSD(Somas dos desvios quadráticos) geral, maximizando a SSD entre grupos ou, alternativamente, minimizando a soma das SSDs dentro dos grupos. A AGR é podada selecionando-se a aresta cuja remoção aumenta ao máximo a função objetivo (dissimilaridade entre grupos).

O processo é repetido até que seja atingido o número de divisões requeridos.

´´´
pygeoda.skater(k, w, data, distance_method='euclidean', bound_vals = [],  min_bound = 0, random_seed=123456789)
´´´


## REDCAP

Bibliotecas: **Pygeoda**

Diferentemente da SKATER, há uma distinção entre a função de ligação(antes ligações simples e completas) e o tratamento de contiguidade.
A distinção entre uma relação de contiguidade fixa e uma matriz de pesos espaciais atualizada é chamada de **FirstOrder** e **FullOrder**.
**Single Linkage** forma a ligação pela menor distância possível, podendo criar árvores muito alongadas, já para **Mean Linkage**, o algoritmo mede a distância entre todos pares(_geralmente euclidiana_), tira a média deles, e os 2 grupos que possuirem menor distância entre si são agrupados, até formar a quantidade de clusters estpulada.
Paralelamente existem outros, como é semelhante ao
**Complete Linkage**, embora se baseie na distância máxima entre os
objetos ou o método do vizinho mais afastado. Neste, a distância entre
dois grupos é calculada entre seus dois pontos mais afastados.


**FullOrder-WardLinkage:**
    Ligação de Ward com pesos espaciais atualizados dinâmicamente.

**FillOrder-MeanLinkage:**
    Comparado aos resultados de Ward, os agrupamentos são mais equilibrados e não há mais agrupamentos isolados. 

**FullOrder_CompleteLinkage**

**FullOrder-SingleLinkage**


Exemplo de uso:

´´´
redcap_clusters = pygeoda.redcap(4, queen_w, data, "fullorder-completelinkage")
redcap_clusters
´´´
