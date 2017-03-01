---
title: Gerar e configurar seu aplicativo de modelos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: 7
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 864963f32fe703ada943f7e5202d7ebf6bf21e51
ms.lasthandoff: 02/22/2017

---
# <a name="generate-and-configure-your-app-from-models"></a>Gerar e configurar o aplicativo por meio de modelos
Você pode gerar ou configurar as partes do seu aplicativo de um modelo.
  
 O modelo representa os requisitos mais diretamente o código. Derivando o comportamento do aplicativo diretamente do modelo, você pode responder a requisitos alterados atualização muito mais rápida e confiável que o código. Embora seja necessário algum trabalho inicial para configurar a derivação, esse investimento é retornado se você espera que as alterações nos requisitos, ou se você planeja fazer diversas variantes do produto.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Gerando o código de seu aplicativo de um modelo  
 É a maneira mais fácil de gerar código usando modelos de texto. Você pode gerar código no mesmo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução na qual você pode manter o modelo. Para obter mais informações, consulte:  
  
-   [Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
-   [Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 Esse método é fácil aplicar incrementalmente. Comece com um aplicativo que funciona somente em um caso específico e escolha algumas partes dele que você deseja variar do modelo. Renomeie os arquivos de origem das partes para que eles se tornem arquivos de modelo (. TT) de texto. Neste ponto, os arquivos de origem. cs serão gerados automaticamente dos arquivos de modelo, portanto, o aplicativo funcionará como antes.  
  
 Em seguida, você pode levar a uma parte do código e substituí-la por uma expressão de modelo de texto, que lê o modelo e gera essa parte do arquivo de origem. Pelo menos um valor do modelo deve gerar a fonte original para que, novamente, você pode executar o aplicativo e ele funcionará como antes. Depois de testar valores diferentes de modelo, você pode mover para inserir expressões de modelo em outra parte do código.  
  
 Esse método incremental significa que a geração de código geralmente é uma abordagem de baixo risco. Os aplicativos resultantes geralmente executam quase, bem como uma versão manuscrita.  
  
 No entanto, se você iniciar com um aplicativo existente, você perceberá que muitos de refatoração é necessário para separar os diferentes comportamentos que são controlados pelo modelo de forma que podem ser variadas independentemente. É recomendável que você avalie esse aspecto do aplicativo quando você estimar o custo de seu projeto.  
  
## <a name="configuring-your-application-from-a-model"></a>Configurar seu aplicativo de um modelo  
 Se você deseja variar o comportamento do aplicativo em tempo de execução, você não pode usar a geração de código, que gera o código-fonte antes do aplicativo é compilado. Em vez disso, você pode projetar seu aplicativo para ler o modelo e variar o comportamento adequadamente. Para obter mais informações, consulte:  
  
-   [Como abrir um modelo partindo de um arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Esse método também pode ser aplicado incrementalmente, mas há mais trabalho no início. Você precisa escrever o código que lê o modelo e configurar uma estrutura que permite que seus valores de estar acessível para as partes de variável. Tornar as partes variável genérico é mais caro do que a geração de código.  
  
 Um aplicativo genérico normalmente executa menos bem que suas contrapartes específicos. Se o desempenho é fundamental, seu plano de projeto deve incluir uma avaliação desse risco.  
  
## <a name="developing-a-derived-application"></a>Desenvolvendo um aplicativo derivado  
 Você pode achar úteis as seguintes diretrizes gerais.  
  
-   **Iniciar específico e generalizar.** Primeiro, grave uma versão específica do seu aplicativo. Essa versão deve funcionar em um conjunto de condições. Quando tiver certeza que ele está funcionando corretamente, você pode fazer com que algumas delas derivam de um modelo. Estenda as partes derivadas gradualmente.  
  
     Por exemplo, crie um site que tem um conjunto específico de páginas da Web antes de criar um aplicativo Web que apresenta páginas que são definidas em um modelo.  
  
-   **Os aspectos de variante do modelo.** Identifique os aspectos que variam entre uma implantação e outro, ou ao longo do tempo como requisitos de alteração. Esses são os aspectos que devem ser derivados de um modelo.  
  
     Por exemplo, se o conjunto de páginas e os links entre eles é alterado, mas o estilo e o formato das páginas é sempre o mesmo, em seguida, o modelo deve descrever os links, mas não tem que descrevem o formato das páginas.  
  
-   **Preocupações separadas.** Se a variável aspectos podem ser divididos em áreas independentes, use modelos separados para cada área. Usando ModelBus, você pode definir as operações que afetam os modelos e as restrições entre eles.  
  
     Por exemplo, use um modelo para definir a navegação entre páginas da Web e um modelo diferente para definir o layout das páginas.
  
-   **O requisito, e não na solução de modelo.** Crie o modelo de forma que ele descreve os requisitos do usuário. Por outro lado, não crie a notação de acordo com as variável aspectos da implementação.  
  
     Por exemplo, o modelo de navegação da Web deve representar páginas da Web e hiperlinks entre eles. O modelo de navegação da Web não deve representar fragmentos de HTML ou classes em seu aplicativo.  
  
-   **Gerar ou interpretar?** Se os requisitos para uma determinada implantação serão alterado raramente, gere código de programa do modelo. Se os requisitos podem mudar com frequência, ou podem coexistir em mais de uma variante da mesma implantação, escreva o aplicativo para que ele pode ler e interpretar um modelo.  
  
     Por exemplo, se você usar o modelo de site da Web para desenvolver uma série de sites da Web diferentes e instalado separadamente, você deve gerar o código do site do modelo. Mas você usa seu modelo para controlar um site que muda diariamente, então é melhor escrever um servidor Web que lê o modelo e apresenta o site adequadamente.  
  
-   **UML ou DSL?** Considere a criação de seu notação de modelagem usando estereótipos estender UML. Defina uma DSL se não houver nenhum diagrama UML que se adapta ao objetivo. Mas evitar que a semântica padrão do UML.  
  
     Por exemplo, um diagrama de classe UML é uma coleção de caixas e setas; com essa notação pode teoricamente definir nada. Mas, não recomendamos que você use o diagrama de classes, exceto onde você está na verdade descrevendo um conjunto de tipos. Por exemplo, você pode adaptar os diagramas de classe para descrever diferentes tipos de páginas da Web.  
  
## <a name="see-also"></a>Consulte também  
 [Gerando código a partir de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
