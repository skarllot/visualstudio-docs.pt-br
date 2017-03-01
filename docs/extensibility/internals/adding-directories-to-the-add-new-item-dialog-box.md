---
title: "Adicionando pastas para a caixa de diálogo Novo Item adicionar | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
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
ms.openlocfilehash: 47167c12bccfc4419c422df128ad188dd86c9e30
ms.lasthandoff: 02/22/2017

---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Adicionando pastas para a caixa de diálogo Novo Item adicionar
O exemplo de código a seguir demonstra como registrar um novo conjunto de diretórios para o **Adicionar Novo Item** caixa de diálogo. Diretórios para o **Adicionar Novo Item** caixa de diálogo são diferentes para cada projeto. Portanto, os diretórios são registrados na subchave projetos, encontrada em \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>O Script de registro  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 O valor Template_Path Especifica o caminho completo do diretório que contém os modelos de projeto. Esses modelos podem ser arquivos. vsz ou arquivos de modelo de um modelo a ser clonado.  
  
 O valor SortPriority Especifica uma prioridade de classificação.  
  
## <a name="adding-items-to-an-existing-project"></a>Adicionando itens a um projeto existente  
 Você também pode adicionar itens a um projeto existente. Por exemplo, para um [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeto, você pode adicionar itens para o \<raiz > pasta \Program Files\Microsoft de \VC#\CSharpProjectItems\LocalProjectItems do Visual Studio. Nesse caso o `%GUID_Project%` é o GUID de um projeto c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Você também pode estender um projeto existente por um subtipo de projeto de programação. Com um subtipo de projeto, você pode estender um projeto sem escrever um novo tipo de projeto. Para obter mais informações sobre os subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionando itens a adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionando pastas a caixa de diálogo Novo projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
