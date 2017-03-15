---
title: "Informações rápidas em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a00eb17193aac6782009d14f5a09fcd831afe7a1
ms.lasthandoff: 02/22/2017

---
# <a name="quick-info-in-a-legacy-language-service"></a>Informações rápidas em um serviço de linguagem herdado
Informações rápidas do IntelliSense mostra informações sobre um identificador de origem quando o usuário coloca o cursor do identificador e seleciona **informações rápidas** do **IntelliSense** menu ou mantém o cursor do mouse sobre o identificador. Isso faz com que uma dica de ferramenta exibida com informações sobre o identificador. Essas informações geralmente consistem o tipo de identificador. Quando o mecanismo de depuração está ativo, essas informações podem incluir o valor atual. O mecanismo de depuração fornece valores de expressão, enquanto o serviço de linguagem manipula somente identificadores.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [passo a passo: exibindo dicas de ferramenta Informaçãorápida](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
 As classes de serviço de linguagem do pacote gerenciado framework (MPF) oferecem suporte completo para exibir a dica de ferramenta informações rápidas do IntelliSense. Tudo o que você precisa fazer é fornecer o texto a ser exibido e habilitar o recurso de informações rápidas.  
  
 O texto a ser exibido é obtido chamando o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Analisador de método com um valor de motivo de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Esse motivo informa ao analisador para obter as informações de tipo (ou o que for apropriado a ser exibido na dica de ferramenta informações rápidas) para o identificador no local especificado no <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto.</xref:Microsoft.VisualStudio.Package.ParseRequest> O <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto é passado para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.ParseRequest>  
  
 O analisador deve analisar tudo até a posição de <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto para determinar os tipos de todos os identificadores.</xref:Microsoft.VisualStudio.Package.ParseRequest> Em seguida, o analisador deve obter o identificador no local da solicitação de análise. Finalmente, o analisador deve passar os dados de dica de ferramenta associados com esse identificador para o <xref:Microsoft.VisualStudio.Package.AuthoringScope>para esse objeto possa retornar o texto a partir do objeto de <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>método.</xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
## <a name="enabling-the-quick-info-feature"></a>Habilitar o recurso de informações rápidas  
 Para habilitar o recurso de informações rápidas, você deve definir o `CodeSense` e `QuickInfo` parâmetros do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>nomeados. Esses atributos definidos a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>e <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>Propriedades.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> </xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
## <a name="implementing-the-quick-info-feature"></a>Implementar o recurso de informações rápidas  
 O <xref:Microsoft.VisualStudio.Package.ViewFilter>classe controla a operação de informações rápidas do IntelliSense.</xref:Microsoft.VisualStudio.Package.ViewFilter> Quando o <xref:Microsoft.VisualStudio.Package.ViewFilter>classe recebe o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>comando, as chamadas de classe de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>e o local do cursor no momento o <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>comando foi enviado.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> </xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> </xref:Microsoft.VisualStudio.Package.ViewFilter> O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método analisador deve, em seguida, analisar a origem até o local especificado e, em seguida, analisar o identificador no local especificado para determinar o que é exibido na dica de ferramenta informações rápidas.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
 A maioria dos analisadores fazer uma análise inicial do arquivo de origem inteiro e armazenam os resultados em uma árvore de análise. A análise completa é executada quando <xref:Microsoft.VisualStudio.Package.ParseReason>é passado para <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.ParseReason> Outros tipos de análise, em seguida, podem usar a árvore de análise para obter as informações desejadas.  
  
 Por exemplo, o valor do motivo de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>pode localizar o identificador no local de origem e procurá-lo na árvore de análise para obter as informações de tipo.</xref:Microsoft.VisualStudio.Package.ParseReason> Essas informações de tipo é então passadas para o <xref:Microsoft.VisualStudio.Package.AuthoringScope>da classe e é retornado pelo <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>método.</xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> </xref:Microsoft.VisualStudio.Package.AuthoringScope>
