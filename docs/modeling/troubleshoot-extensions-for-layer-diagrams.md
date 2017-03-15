---
title: "Solucionar problemas de extensões para diagramas de dependência | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
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
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Solucionar problemas de extensões para diagramas de dependência
Este tópico aborda alguns problemas que você pode encontrar ao criar camada extensões do modelo.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Quando pressiono F5 para depurar a extensão my, Meus comandos, manipuladores de gestos, extensões de validação ou propriedades personalizadas não aparecem em diagramas de dependência na instância Experimental do[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Abra sua solução de extensão na instância Experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e na **criar** menu, clique em **recompilar solução**.  
  
2.  Pressione **F5** ou **CTRL + F5** para iniciar a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Abra um diagrama de dependência e testar sua extensão.  
  
 Continue com o próximo procedimento, se necessário.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Executa uma versão antiga da extensão my.  
  
1.  Verifique se nenhuma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está em execução.  
  
2.  Exclua a seguinte pasta: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [version]  
  
    > [!NOTE]
    >  % LocalAppData % é normalmente *DriveName*: \Users\\*nome de usuário*\AppData\Local.  
  
 Continue com o próximo procedimento, se necessário.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Uma versão antiga do meus resultados de validação aparece ou meu método de validação não for chamado.  
  
1.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no **criar** menu, clique em **limpar solução**. Isso limpa os resultados da análise de validação anterior em cache.  
  
2.  Certifique-se de que as camadas no seu modelo estão associadas a elementos de código e que há pelo menos um link de dependência no modelo. Validação não é invocada se não há nada para validar.  
  
3.  Pontos de interrupção regulares não podem funcionar em um método de validação, porque ele é executado em um processo separado. Você deve inserir uma chamada a `System.Diagnostics.Debugger.Launch()` se você deseja depurar seu método.  
  
4.  Em **source.extension.vsixmanifest** em seu projeto de validação de camada, certifique-se de que você tenha adicionado ambos um **componente MEF** item e um **tipo de extensão personalizada** item sob **conteúdo**.  
  
## <a name="see-also"></a>Consulte também  
 [Estender a diagramas de dependência](../modeling/extend-layer-diagrams.md)

