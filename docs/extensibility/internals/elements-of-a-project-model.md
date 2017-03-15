---
title: Elementos de um modelo de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
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
ms.openlocfilehash: 6dcf09efb1f67fa5b076111b2ea61ca28261fc84
ms.lasthandoff: 02/22/2017

---
# <a name="elements-of-a-project-model"></a>Elementos de um modelo de projeto
As interfaces e as implementações de todos os projetos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compartilham uma estrutura básica: o modelo de projeto para o tipo de projeto. Em seu modelo de projeto, que é o VSPackage que você está desenvolvendo, você cria objetos que atendam suas decisões de design e trabalham em conjunto com a funcionalidade global fornecida pelo IDE. Embora você controlar como um item de projeto é mantido, por exemplo, você não controlar as notificações que um arquivo deve ser persistente. Quando um usuário coloca o foco em um item de projeto aberto e escolhe **salvar** sobre o **arquivo** menu o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de menus, seu código de tipo de projeto deve interceptar o comando a partir do IDE, manter o arquivo e enviar notificação para o IDE que o arquivo é não seja alterado.  
  
 O VSPackage interage com o IDE por meio de serviços que fornecem acesso às interfaces do IDE. Por exemplo, por meio de serviços específicos, você monitorar e rota comandos e fornece informações de contexto para seleções feitas no projeto. Toda a funcionalidade IDE global necessária para o VSPackage é fornecida pelos serviços. Para obter mais informações sobre serviços, consulte [como: obter um serviço](../../extensibility/how-to-get-a-service.md).  
  
 Outras considerações de implementação:  
  
-   Um modelo de projeto único pode conter mais de um tipo de projeto.  
  
-   Tipos de projeto e as fábricas do Assistente do projeto são registradas independentemente com GUIDs.  
  
-   Cada projeto deve ter um arquivo de modelo ou o Assistente para inicializar o novo arquivo de projeto quando um usuário cria um novo projeto por meio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário. Por exemplo, o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelos inicializar o que eventualmente se tornarem arquivos. vcproj.  
  
 A ilustração a seguir mostra as interfaces principais, serviços e objetos que compõem uma implementação típica do projeto. Você pode usar o auxiliar de aplicativo, HierUtil7, para criar os objetos subjacentes e outro clichê de programação. Para obter mais informações sobre o auxiliar do aplicativo HierUtil7, consulte [fora da compilação: usando Classes do projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Gráfico de modelo de projeto do Studio Visual](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
Modelo de projeto  
  
 Para obter mais informações sobre as interfaces e serviços listados no diagrama anterior e outras interfaces opcionais não são incluídos no diagrama, consulte [componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md).  
  
 Projetos pode oferecer suporte a comandos e, portanto, deve implementar a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface participem de roteamento de comando por meio do contexto do comando GUIDs.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Não na compilação: usando Classes do projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)   
 [Criação de instâncias de projetos usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Como: obter um serviço](../../extensibility/how-to-get-a-service.md)   
 [Criando tipos de projeto](../../extensibility/internals/creating-project-types.md)
