---
title: Quando criar tipos de projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
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
ms.openlocfilehash: ce0cc722c26fd800b0f8120d272a999d9d04e819
ms.lasthandoff: 02/22/2017

---
# <a name="when-to-create-project-types"></a>Quando criar tipos de projeto
Criar um novo tipo de projeto fornece uma base para a personalização [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para seus usuários. No entanto, criar um novo tipo de projeto não é necessário para todos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizações. As diretrizes a seguir devem ajudá-lo a determinar se um novo tipo de projeto é necessário para seu cenário.  
  
## <a name="create-a-new-project-type"></a>Criar um novo tipo de projeto  
 Você deve criar um tipo de projeto se desejar personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para atuar em uma ou mais das seguintes maneiras:  
  
-   Participar de compilação, implantar, configurações e controle de origem.  
  
-   Oferece suporte à depuração.  
  
-   Exibir itens de projeto no **Solution Explorer**.  
  
-   Use o **Abrir projeto** ou **novo projeto** caixa de diálogo.  
  
-   Suporte a aninhamento de projeto.  
  
## <a name="extend-an-existing-project-type"></a>Estender um tipo de projeto existente  
 Você talvez queira criar um novo tipo de projeto que pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das seguintes maneiras para modificar ou estender o comportamento de um tipo de projeto existente, por exemplo, modificando o processo de compilação [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projetos:  
  
-   Trabalhar com vários arquivos como uma única unidade.  
  
-   Exiba um único arquivo como uma hierarquia de subelementos.  
  
-   Exiba um contexto de comando em torno de editores.  
  
-   Exiba um contexto de serviço para editores.  
  
## <a name="use-an-existing-project-type"></a>Usar um tipo de projeto existente  
 Criar um novo projeto, às vezes, não é necessário. A tabela a seguir mostra as tarefas que você não precisa criar um tipo de projeto para.  
  
|Tarefa|Descrição|  
|----------|-----------------|  
|Tratamento de comandos|Qualquer VSPackage pode manipular comandos.|  
|Criar um editor|Editores personalizados podem ser registrados. Para obter mais informações, consulte [editores e janelas de documento](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Propriedade windows|Você pode criar janelas de ferramenta e de documentos sem adicionar um novo tipo de projeto.|  
|Expondo propriedades na janela Propriedades|Todos os objetos podem expor propriedades.|  
  
## <a name="create-a-project-subtype"></a>Criar um subtipo de projeto  
 Você pode usar os subtipos de projeto para estender um tipo de projeto gerenciado sem precisar criar um novo tipo de projeto. Subtipos de projeto usam agregação COM estender projetos gerenciados escritos em Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Com a agregação de COM, você pode reutilizar grande parte da implementação do sistema de projeto gerenciado e ainda personalizar para um cenário particular por meio de agregação e o uso do suporte a interfaces. Para obter mais informações sobre os subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Editores e janelas de documento](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
