---
title: Projetos de exemplo das Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Projetos de exemplo das Ferramentas do R para Visual Studio

Essa coleção de exemplos oferece uma introdução ao R, às RTVS (Ferramentas do R para Visual Studio) e ao Microsoft R Server:

1. Baixe o [arquivo zip de exemplo](https://github.com/Microsoft/RTVS-docs/archive/master.zip) e extraia em uma pasta da sua escolha.
1. Abra `examples/Examples.sln`. Você verá duas pastas do projeto:

    - *A First Look at R* (Uma introdução ao R) fornece uma introdução fácil para principiantes em R.
    - *MRS and Machine Learning* (SRS e aprendizado de máquina) dá exemplos de como usar o R e o Microsoft R Server para aprendizado de máquina.

## <a name="a-first-look-at-r"></a>A First Look at R (Uma introdução ao R)

Este exemplo fornece uma introdução detalhada ao R por meio de comentários extensos nos arquivos de origem. A melhor maneira de usá-los é colocar o cursor na parte superior do arquivo, em seguida, pressionar Ctrl + Enter para enviar cada linha, uma de cada vez, para a janela **R Interativo** em que os resultados são exibidos. Observe que algumas linhas instalarão pacotes, o que poderá demorar um minuto ou dois.

- `1-Getting Started with R.R` aborda vários conceitos básicos do R incluindo o uso de pacotes, carregamento e análise de dados e criação de gráficos.

    ![Exemplo de saída de 1-Getting Started with R.R (1 – Introdução ao R.R)](~/docs/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` apresenta o pacote gráfico ggplot2 conhecido por seus gráficos atraentes e sua sintaxe simples. Este exemplo visualiza dados de terremoto de Fiji.

    ![Exemplo de saída de 2-Introduction to ggplot2.R (2 – Introdução ao ggplot2.R)](~/docs/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server and Machine Learning (Microsoft R Server e aprendizado de máquina)

Esta coleção de exemplos mostra como usar o R e o Microsoft R Server para criar modelos de aprendizado de máquina e como aproveitar as funcionalidades do [MRS (Microsoft R Server)](http://aka.ms/rtvs-msft-r). Observe que você precisará instalar o MRS para executar scripts com `MRS` no título e onde indicado.

Como todos os exemplos, uma ótima maneira de experimentá-los é abrir o arquivo, colocar o cursor na parte superior e, em seguida, percorrer o código linha por linha com Ctrl + Enter. Consulte também os arquivos de markdown em cada pasta para obter detalhes adicionais.

- `Benchmarks` executa inúmeros parâmetros de comparação de computação intensiva para mostrar os ganhos de desempenho possíveis por meio do uso do Microsoft R Open e da Intel MKL (Math Kernel Library) para cálculos de álgebra linear rápidos e paralelos. Com os dados simulados, ele compara especificamente usando dois threads em relação a um para determinados cálculos relacionados à matriz.   

    ![Gráfico de parâmetro de comparação de exemplo](~/docs/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` cria um modelo de previsão de demanda para locações de bicicletas com base em um conjunto de dados históricos, usando o Microsoft R Server. 

- `Data_Exploration` contém três scripts:  
    - `Import Data from URL.R` mostra como carregar um arquivo de dados identificado por URL no R.
    - `Import Data from URL to xdf.R` mostra como carregar um arquivo de dados identificado por URL no Microsoft R Server como um xdf. (Requer o MRS.)
    - `Using ggplot2.R` é uma extensão do exemplo `A First Look at R/2-Introduction to ggplot2.R`, fazendo um tour mais amplo da funcionalidade do ggplot2, incluindo a criação de gráficos 3D interativos.

        ![Exemplo de saída usando o ggplot2.R](~/docs/rtvs/media/samples-3d-interactive.png)

- `Datasets` contém três arquivos `.csv` usados por outros exemplos
- `Flight_Delays_Prediction_with_R` e `Flight_Delays_Prediction_with_MRS` mostram como prever atrasos de voo usando R, aprendizado de máquina e desempenho e dados meteorológicos pontuais históricos. 
- `Machine learning` contém três exemplos de aprendizado para prever atrasos de voo, preços de habitação e aluguéis de bicicletas, demonstrando a aplicação do R e do MRS a problemas do mundo real. Eles também mostram como usar vários modelos de aprendizado de máquina populares e implantá-los como um serviço Web do Azure usando um espaço de trabalho do [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` é uma comparação de seis partes que mostra as semelhanças e diferenças entre R, Microsoft R Open e Microsoft R Server com comandos, sintaxe, constructos e desempenho.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>O que o Microsoft R Open e o Microsoft R Server têm de especial?

O [Microsoft R Open](http://aka.ms/rtvs-r-open), a distribuição do R da Microsoft, é diferente do [CRAN R](https://cran.r-project.org/) de duas maneiras importantes:

1. [Melhor desempenho de computação](https://mran.revolutionanalytics.com/rro/#intelmkl1) quando usado com as [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl). Eles estão disponíveis como um download gratuito da Microsoft para ser usado com o Microsoft R Open.

1. [Kit de ferramentas do R reproduzível](https://mran.revolutionanalytics.com/rro/#reproducibility), que garante que as bibliotecas usadas para criar o programa R estejam sempre disponíveis para outras pessoas que deseja reproduzir seu trabalho.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) é uma extensão do R que permite lidar com mais dados e com mais rapidez. Ele oferece ao R dois recursos avançados:

1. Conjuntos de dados maiores. O MRS pode processar dados fora da memória de uma variedade de fontes incluindo clusters Hadoop, bancos de dados e data warehouses. Você nunca mais precisará ficar limitado pela RAM novamente.

1. Processamento paralelo, de vários núcleos. O MRS pode distribuir a computação com eficiência em todos os recursos computacionais que tem disponíveis. Em sua estação de trabalho pessoal ou em um cluster remoto, o MRS obterá uma resposta mais rápida.

A comparação a seguir mostra que o MRS e o MRO com MKL têm um desempenho de computação significativamente melhor em relação a um certo cálculo da matriz de R e MRO sem MKL. São usados dados simulados no cálculo:

![Comparando o MRS e MRO com MKL ao R e ao MRO sem MKL](~/docs/rtvs/media/samples-speed-comparison.png)

Para obter uma comparação técnica do R com o MRO e o MRS, confira [a discussão detalhada do Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sobre o tópico.

A figura a seguir compara o tempo decorrido em segundos usado na criação de modelos de regressão logística para prever se a chegada dos voos de passageiros agendados atrasará mais de 15 minutos. O tempo decorrido usado em CRAN R aumenta drasticamente ao aumentar um pequeno número de linhas, enquanto o MRS aumenta apenas cerca de duas vezes. Para obter detalhes sobre esse parâmetro de comparação, confira o exemplo `Benchmarks/rxGlm_benchmark.R`.

![Parâmetro de comparação rxGlm](~/docs/rtvs/media/samples-rxGLM-benchmark.png)

