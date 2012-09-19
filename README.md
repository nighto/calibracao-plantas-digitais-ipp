calibracao-plantas-digitais-ipp
===============================

Coleção de arquivos de calibração do PicLayer/JOSM (.cal) para as Plantas Digitais do IPP

O que são arquivos .cal
-----------------------

Os arquivos .cal são arquivos de calibração gerados pelo plugin [PicLayer](http://wiki.openstreetmap.org/wiki/JOSM/Plugins/PicLayer) do [JOSM](http://josm.openstreetmap.de/), um editor de mapas do [OpenStreetMap](http://openstreetmap.org/).

A que se referem estes arquivos .cal
------------------------------------

Os arquivos de calibração deste repositório são referentes aos arquivos de Plantas Digitais disponibilizados no [Portal Geo Rio do IPP](http://portalgeo.rio.rj.gov.br/portalgeo/index.asp). 

Como baixar as plantas digitais originais e convertê-las para uso no JOSM
-------------------------------------------------------------------------

As plantas digitais estão disponibilizadas no servidor do Portal Geo Rio como arquivos wmf zipados. No repositório, há um arquivos `plantas-digitais.txt` que pode ser utilizado para baixar em lote todos os arquivos:

    wget -i plantas-digitais.txt

Este comando irá baixar um total de 63 arquivos `.zip`. Você poderá extrai-los todos com:

    unzip *.zip

E apagar os arquivos originais com:

    rm *.zip

Os arquivos PDF não podem ser utilizados diretamente pelo PicLayer, devendo primeiro serem convertidos para jpeg ou png. **Usamos por padrão a densidade de 600.**

    convert -density 600 mapa.wmf mapa.jpg

O argumento `-density 600` garante que as letras do mapa continuem visíveis no JOSM. O convert é um pacote do [ImageMagick](http://www.imagemagick.org/).

Se preferir converter todos os arquivos de uma só vez,

    for i in *wmf ; do convert -density 600 $i `basename $i .wmf`.jpg ; done

No JOSM, posicione as coordenadas mais ou menos na região de onde seria o mapa, selecione a aba PicLayer e carrege o mapa.jpg.

Agora vem a parte mais chatinha que é calibrar o mapa. Como os mapas do IBGE vem com as latitudes/longitudes dá para marcar os pontos e arrastá-los. Requer um pouquinho de prática, mas uma vez que está feito ele salva a calibração num arquivo mapa.jpg.cal e fica pronto. No site do PicLayer tem um tutorial de como isto é feito (http://wiki.openstreetmap.org/wiki/JOSM/Plugins/PicLayer).