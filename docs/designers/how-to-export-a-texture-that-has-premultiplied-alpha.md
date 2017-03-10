---
title: "Como exportar uma textura que tenha Alfa pr&#233;-multiplicado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 4
caps.handback.revision: 4
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Como exportar uma textura que tenha Alfa pr&#233;-multiplicado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Pipeline de Conteúdo da Imagem pode gerar texturas alfa pré\-multiplicadas de uma imagem de origem.  Elas podem ser mais simples de usar e mais robustas do que as texturas que não contêm o alfa pré\-multiplicado.  
  
 Este documento demonstra estas atividades:  
  
-   Configurando a imagem de origem a ser processada pelo Pipeline de Conteúdo da Imagem.  
  
-   Configurando o Pipeline de Conteúdo de Imagem para gerar alfa pré\-multiplicado.  
  
## Alfa pré\-multiplicado  
 O alfa pré\-multiplicado oferece várias vantagens sobre o alfa não pré\-multiplicado convencional, porque representa melhor a interação do mundo real da luz com os diretórios físicos materiais separando a contribuição de cor de texel \(a cor que adiciona à cena\) de sua translucência \(quantidade de cor subjacente que permite completamente\).  Algumas das vantagens de usar o alfa pré\-multiplicado são:  
  
-   A combinação com o alfa pré\-multiplicado é uma operação associativa; o resultado de misturar mais texturas translúcidas é o mesmo, independentemente da ordem em que texturas são misturadas.  
  
-   Devido à natureza associativa de combinação com o alfa pré\-multiplicado, a renderização de várias passagens dos objetos translúcidos é simplificada.  
  
-   Usando o alfa pré\-multiplicado, tanto a combinação puramente aditiva \(configurando alfa para zero\) e a combinação interpolar linearmente podem ser alcançadas simultaneamente.  Por exemplo, em um sistema de partícula, uma partícula de fogo aditivamente combinada pode se tornar uma partícula de fumaça translúcida combinada usando interpolação linear.  Sem alfa pré\-multiplicado, você teria que desenhar as partículas de fogo separadamente das partículas de fumaça, e alterar o estado de renderização entre chamadas de desenho.  
  
-   As texturas que usam a compressão alfa pré\-multiplicada com qualidade mais alta do que as que não usam essa compressão e que não exibem o efeito de borda descolorida ou "aura", que pode ocorrer quando você mistura texturas que não usam alfa pré\-multiplicada.  
  
#### Para criar uma textura que usa um alfa pré\-multiplicado  
  
1.  Comece com uma textura básica.  Carregue um arquivo de imagem existente ou crie um como descrito em [Como: criar uma textura básica](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  
  
2.  Configure o arquivo de textura de modo que seja processado pelo Pipeline de Conteúdo de Imagem.  No **Gerenciador de Soluções**, abra o menu de atalho para o arquivo de textura e, em seguida, selecione **Propriedades**.  Na página **Propriedades de Configuração**, **Geral**, defina a propriedade de **Tipo de Item** para **Pipeline de conteúdo de imagem**.  Certifique\-se de que a propriedade **Conteúdo** esteja definido como **Sim** e **Excluir de Compilação** esteja definido como **Não** e então escolha o botão **Aplicar**.  A página de propriedades de configuração **Pipeline de Conteúdo da Imagem** é exibida.  
  
3.  Configure o Pipeline de Conteúdo de Imagem para gerar alfa pré\-multiplicado.  Na página **Propriedades de Configuração**, **Pipeline de Conteúdo de Imagem**, **Geral**, defina a propriedade de **Converter o formato alfa pré\-multiplicado** para **Sim \(\/generatepremultipliedalpha\)**.  
  
4.  Escolha o botão **OK**.  
  
 Quando você criar o projeto, o pipeline de conteúdo da imagem converte a imagem de origem de formato trabalhando no formato de saída que você especificou \(isso inclui a conversão da imagem para um formato alfa pré\-multiplicado\) e o resultado é copiado para o diretório de saída do projeto.