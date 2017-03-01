---
title: Interface de assistente (IDTWizard) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
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
ms.openlocfilehash: 02a0932f26897542c3a8aee8aa91e9f739f4fc1c
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-interface-idtwizard"></a>Interface de assistente (IDTWizard)
O ambiente de desenvolvimento integrado (IDE) usa o <xref:EnvDTE.IDTWizard>interface para se comunicar com assistentes.</xref:EnvDTE.IDTWizard> Assistentes devem implementar essa interface para ser instalado no IDE.  
  
 O <xref:EnvDTE.IDTWizard.Execute%2A>é o único método associado com o <xref:EnvDTE.IDTWizard>interface.</xref:EnvDTE.IDTWizard> </xref:EnvDTE.IDTWizard.Execute%2A> Assistentes de implementam esse método e o IDE chama o método na interface. O exemplo a seguir mostra a assinatura do método.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 O mecanismo de início é semelhante para ambos os **novo projeto** e **Adicionar Novo Item**assistentes. Para começar, você chama o <xref:EnvDTE.IDTWizard>interface definida em Dteinternal.h.</xref:EnvDTE.IDTWizard> A única diferença é o conjunto de contexto e parâmetros personalizados que são passados para a interface quando a interface é chamada.  
  
 As seguintes informações descrevem o <xref:EnvDTE.IDTWizard>interface assistentes devem implementar para trabalhar no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.</xref:EnvDTE.IDTWizard> O IDE chama o <xref:EnvDTE.IDTWizard.Execute%2A>método no assistente, passando o seguinte:</xref:EnvDTE.IDTWizard.Execute%2A>  
  
-   O objeto DTE  
  
     O objeto DTE é a raiz do modelo de automação.  
  
-   O identificador para a caixa de diálogo janela conforme o segmento de código `hwndOwner ([in] long)`.  
  
     O assistente utiliza `hwndOwner` como o pai para a caixa de diálogo do assistente.  
  
-   Parâmetros de contexto passado para a interface como variante para SAFEARRAY conforme mostrado no segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parâmetros de contexto contém uma matriz de valores que são específicos para o tipo de assistente que está sendo iniciado e o estado atual do projeto. O IDE passa os parâmetros de contexto para o assistente. Para obter mais informações, consulte [parâmetros de contexto](../../extensibility/internals/context-parameters.md).  
  
-   Parâmetros personalizados passado para a interface como uma variante para SAFEARRAY conforme mostrado no segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parâmetros personalizados contêm uma matriz de parâmetros definidos pelo usuário. Um arquivo. vsz passa parâmetros personalizados para o IDE. Os valores são determinados pelo `Param=` instruções. Para obter mais informações, consulte [parâmetros personalizados](../../extensibility/internals/custom-parameters.md).  
  
-   São valores de retorno para a interface  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
