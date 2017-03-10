---
title: "Desenhe as formas e demarcadores | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Desenhe as formas e demarcadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No Designer XAML, um *forma* é exatamente o que você esperaria. Por exemplo: um retângulo, um círculo ou uma elipse. Um *caminho* é uma versão mais flexível de uma forma. Você pode fazer coisas como reformatá\-los ou reuni\-los às novas formas de formulário.  
  
 Formas e caminhos usam gráficos vetoriais, portanto, eles se adapta bem a monitores de alta resolução. Se você quiser saber mais sobre gráficos de vetor, consulte [o que são gráficos vetoriais](https://www.youtube.com/watch?v=MoCSwF0n-io) ou [gráficos vetoriais](http://www.webopedia.com/TERM/V/vector_graphics.html).  
  
 **Neste tópico:**  
  
-   [Desenhar uma forma](#Shape)  
  
-   [Desenhar um caminho](#Path)  
  
-   [Converter uma forma em um demarcador](#Convert)  
  
-   [Combinar caminhos](#Combine)  
  
-   [Criar um caminho composto](#Compound)  
  
-   [Criar um caminho de recorte](#Clipping)  
  
##  <a name="Shape"></a> Desenhar uma forma  
 Você pode encontrar formas de **ativos** painel.  
  
 ![Shapes category on the Assets panel](../designers/media/b4_shapes_assetspanel.png "b4\_Shapes\_AssetsPanel")  
  
 Arraste qualquer forma desejada para a prancheta. Em seguida, você pode usar identificadores na forma para dimensionar, girar, mover ou distorcer a forma.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83\-3091\-4490\-ab58\-4218b188439e")  
  
##  <a name="Path"></a> Desenhar um caminho  
 Um caminho é uma série de linhas e curvas conectadas. Use um caminho para criar formas interessantes que não estão disponíveis na **ativos** painel.  
  
 Você pode desenhar um caminho por meio de uma linha, caneta ou um lápis. Você pode encontrar essas ferramentas no **ferramentas** painel.  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8\-b6a5\-4e37\-8af3\-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21\-be83\-4cf6\-903b\-3a49f00c9860")  
  
### Desenhar uma linha reta  
 Use o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54"), ou **linha** ferramenta ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397\-5283\-48be\-8396\-3449be7b6fbf").  
  
 **Usando a ferramenta Caneta** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54")  
  
 Na prancheta, clique uma vez para definir o ponto inicial e, em seguida, clique novamente para definir o final da linha.  
  
 **Usando a ferramenta de linha** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397\-5283\-48be\-8396\-3449be7b6fbf")  
  
 Na prancheta, arraste de onde você deseja iniciar a linha e solte\-o no ponto onde você deseja que a linha termine.  
  
### Desenhar uma curva  
 Use o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 Na prancheta, clique uma vez para definir o ponto inicial de uma linha e, em seguida, clique e arraste o ponteiro para criar a curva desejada.  
  
 Se você quiser fechar o caminho, clique no primeiro ponto na linha.  
  
### Alterar a forma de uma curva  
 Use o **Seleção direta** ferramenta ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f\-c116\-451d\-8dd2\-1f88b8406362").  
  
 Clique na forma e, em seguida, arraste qualquer ponto na forma de alterar as formas.  
  
### Desenhar um demarcador de forma livre  
 Use o **Lápis** ferramenta ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167\-734f\-46c9\-b012\-987ee63450cd").  
  
 Na prancheta, desenhe um caminho de forma livre como faria usando um lápis real.  
  
### Remover a parte de um caminho  
 Use o **Seleção direta** ferramenta ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f\-c116\-451d\-8dd2\-1f88b8406362").  
  
 Selecione o caminho que contém o segmento que deseja excluir e, em seguida, clique o **Excluir** botão.  
  
### Remover um ponto em um caminho  
 Use o **seleção** ferramenta  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa"), e o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 Use o **seleção** ferramenta  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") para selecionar o caminho. Em seguida, use o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54") ao clicar no ponto em que você deseja remover.  
  
### Adicionar um ponto em um caminho  
 Use o **seleção** ferramenta  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa"), e o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 Use o **seleção** ferramenta  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") para selecionar o caminho. Use o **caneta** ferramenta ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54") clique em qualquer lugar no caminho de onde você deseja adicionar o ponto.  
  
##  <a name="Convert"></a> Converter uma forma em um demarcador  
 Para modificar uma forma da mesma forma que você modifique um caminho, convertê\-la em um caminho.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [trabalhar com caminhos: converter uma forma em um caminho](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
##  <a name="Combine"></a> Combinar caminhos  
 Você pode combinar formas e caminhos em um único caminho.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d\-a338\-4ef4\-96c5\-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1_1.png "B1\_1")|Duas formas antes da combinação|![](../designers/media/b1_4.png "B1\_4")|Intersect|  
|![](../designers/media/b1_2.png "B1\_2")|Unir|![](../designers/media/b1_5.png "B1\_5")|Excluir sobreposição|  
|![](../designers/media/b1_3.png "B1\_3")|Dividir|![](../designers/media/b1_6.png "B1\_6")|Subtrair|  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [trabalhar com caminhos: combinar caminhos](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
##  <a name="Compound"></a> Criar um caminho composto  
 Quando você cria um caminho composto, as partes de interseção dos caminhos são subtraídas do resultado e o caminho resultante assume as propriedades visuais do caminho mais baixo.  
  
 Você pode separar um caminho composto qualquer momento depois de criá\-la.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa\-d9a7\-4de4\-8de5\-b10d28f08a84")  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [trabalhar com caminhos: criar um caminho composto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
##  <a name="Clipping"></a> Criar um caminho de recorte  
 Um caminho de recorte é um caminho ou uma forma que é aplicada a outro objeto, ocultando as partes do objeto mascarado que estão fora do caminho de recorte.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98\-a841\-4f39\-a3ef\-36090cf5a625")  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [trabalhar com caminhos: criar um caminho de recorte](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## Consulte também  
 [Criando uma interface de usuário usando o Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)