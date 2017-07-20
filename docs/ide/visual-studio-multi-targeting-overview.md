---
title: "Visão geral do Visual Studio Multi-Targeting | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 93e0c6676d48a0164dcf3b184bcb886934372787
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="visual-studio-multi-targeting-overview"></a>Visão geral de multissegmentação do Visual Studio
Nesta versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], é possível especificar a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] necessária para seu aplicativo. Portanto, se você desejar usar essa versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para continuar desenvolvendo um projeto iniciado em uma versão anterior, não será necessário alterar o destino da estrutura. Também é possível criar uma solução que contém projetos que têm como destino versões diferentes da estrutura. A definição de destino da estrutura também ajuda a assegurar que o aplicativo use apenas a funcionalidade disponível na versão especificada da estrutura.  
  
> [!TIP]
>  Também é possível definir aplicativos como destino para plataformas diferentes. Para obter mais informações, consulte [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)  
  
## <a name="framework-targeting-features"></a>Recursos de definição de destino da estrutura  
 A definição de destino da estrutura inclui os seguintes recursos:  
  
-   Ao abrir um projeto que tem como destino uma versão anterior do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] pode atualizá-lo ou deixar o destino no estado em que se encontra.  
  
-   Ao criar um projeto, é possível especificar a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que você deseja definir como destino.  
  
-   É possível alterar a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que um projeto existente tem como destino.  
  
-   É possível definir como destino uma versão diferente do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] em cada um dos vários projetos na mesma solução.  
  
-   Ao alterar a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que um projeto tem como destino, o [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] faz as alterações necessárias nas referências e nos arquivos de configuração.  
  
 Ao trabalhar em um projeto que tem como destino uma versão anterior do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o Visual Studio altera dinamicamente o ambiente de desenvolvimento, da seguinte maneira:  
  
-   Ele filtra os itens das caixas de diálogo **Novo Projeto**, **Adicionar Novo Item**, **Adicionar Nova Referência** e **Adicionar Referência de Serviço** para omitir as opções que não estão disponíveis na versão de destino.  
  
-   Ele filtra os controles personalizados da **Caixa de ferramentas** para remover aqueles que não estão disponíveis na versão de destino e mostrar somente os controles mais atualizados quando vários controles estão disponíveis.  
  
-   Ele filtra o IntelliSense para omitir os recursos de idioma que não estão disponíveis na versão de destino.  
  
-   Ele filtra as propriedades na janela **Propriedades** para omitir aquelas que não estão disponíveis na versão de destino.  
  
-   Ele filtra as opções de menu para omitir as opções que não estão disponíveis na versão de destino.  
  
-   Para builds, ele usa a versão do compilador e as opções do compilador apropriadas para a versão de destino.  
  
> [!NOTE]
>  A definição de destino da estrutura não assegura que o aplicativo será executado corretamente. É necessário testar o aplicativo para ter certeza de que ele é executado na versão de destino. Não é possível definir como destino versões de estrutura anteriores ao .NET Framework 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Selecionando uma versão de estrutura de destino  
 Ao criar um projeto, selecione a versão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino na caixa de diálogo **Novo Projeto**. A lista de modelos de projeto disponíveis é filtrada com base na seleção. Em um projeto existente, é possível alterar a versão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino na caixa de diálogo das propriedades do projeto. Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  Nas edições Express do Visual Studio, não é possível definir a estrutura de destino na caixa de diálogo **Novo Projeto**.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Resolvendo referências de assembly do sistema e do usuário  
 Para definir uma versão do .NET Framework como destino, é necessário primeiro instalar as referências de assembly apropriadas. As referências de assembly do .NET Framework versões 2.0, 3.0 e 3.5 são incluídas no .NET Framework 3.5 SP1, que podem ser baixadas no [Centro de Download da Microsoft, site do Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602). As referências de assembly do .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile e Silverlight também estão disponíveis no site [Downloads do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Um perfil de cliente do .NET Framework é um subconjunto do .NET Framework que fornece um conjunto limitado de bibliotecas e recursos. Para obter mais informações sobre perfis de cliente, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 A caixa de diálogo **Adicionar Referência** desabilita assemblies do sistema que não pertencem à versão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino, para que eles não possam ser adicionados a um projeto acidentalmente. (Assemblies do sistema são arquivos .dll incluídos em uma versão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) As referências que pertencem a uma versão do Framework posterior à versão de destino não serão resolvidas e os controles que dependem dessa referência não podem ser adicionados. Se você desejar habilitar essa referência, redefina o destino [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] do projeto para um que inclua a referência.  Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
 Para obter mais informações sobre referências de assembly, consulte [Resolvendo assemblies em tempo de design](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Habilitando o LINQ  
 Ao definir o .NET Framework 3.5 ou posterior como destino, uma referência ao System.Core e uma importação no nível do projeto para System.Linq (somente no Visual Basic) são adicionadas automaticamente. Se você desejar usar recursos do LINQ, também será necessário ativar a Opção Infer (somente no Visual Basic). A referência e a importação serão removidas automaticamente se você alterar o destino para uma versão anterior do .NET Framework. Para saber mais, consulte [Trabalhando com LINQ](/dotnet/csharp/tutorials/working-with-linq).  
  
## <a name="see-also"></a>Consulte também  
 [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)   
 [Compatibilidade com plataformas e requisitos do sistema](http://www.microsoft.com/visualstudio/eng/products/compatibility)
