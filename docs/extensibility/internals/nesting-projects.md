---
title: Projetos de aninhamento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
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
ms.openlocfilehash: b82a4251f51afdd86974288e970084315439a480
ms.lasthandoff: 02/22/2017

---
# <a name="nesting-projects"></a>Projetos de aninhamento
Os desenvolvedores de aplicativos corporativos que usam o pacote do VS convenientemente podem agrupar tipos semelhantes de projetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando *aninhamento de projeto*. Por exemplo, o projeto de modelo corporativo usa projetos aninhados para agrupar projetos em categorias. Projetos de fachada de negócios, projetos de interface do usuário da Web e assim por diante são agrupados em uma categoria.  
  
 Nesse cenário, não há nenhum limite para o número de projetos, que o desenvolvedor pode aninhar em cada projeto pai, embora o desenvolvedor pode fornecer programaticamente limites. Esse tipo de agrupamento pode ser feito também recursiva, caso em que os projetos do mesmo tipo como um projeto filho podem ser aninhados sob o filho para se tornar um subprojeto do filho, que é um subprojeto do pai.  
  
 Aninhamento de projeto não é uma parte intrínseca da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Você precisa escrever o código para habilitar o aninhamento e subprojeto aninhamento em projetos do filho. O projeto pai é um VSPackage especial ou tipo de projeto, criado e registrado com seu próprio GUID que inclui o código que é necessário para implementar o aninhamento de projeto.  
  
 Você pode encontrar um exemplo de projetos aninhados no exemplo do c# Example.Nested projeto.  
  
## <a name="nested-projects-example"></a>Exemplo de projetos aninhados  
 ![Solução de projetos aninhados](~/extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Exemplo de projetos aninhados  
  
## <a name="see-also"></a>Consulte também  
 [Como: implementar projetos aninhados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerações para descarregando e recarregando projetos aninhados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Suporte do Assistente para projetos aninhados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementar manipulação de comando para projetos aninhados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [A caixa de diálogo AddItem de filtragem para projetos aninhados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
