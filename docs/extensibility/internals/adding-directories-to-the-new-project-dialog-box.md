---
title: "Adicionando pastas a caixa de diálogo Novo projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
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
ms.openlocfilehash: ea2b117cfd346a73653ef8d9a776d711e235ff30
ms.lasthandoff: 02/22/2017

---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Adicionando pastas a caixa de diálogo Novo projeto
Quando você cria novos tipos de projeto, você também pode registrar um novo diretório no **novo projeto** caixa de diálogo para exibi-los para uso como modelos. O exemplo de código a seguir explica como registrar um novo diretório, também conhecido como um nó. No exemplo, modelos expostos pelo VSPackage CLSID_Package são registrados. Como resultado, o lado esquerdo do **novo projeto** caixa de diálogo oferece o nó adicional, com um nome determinado pelo recurso Folder_Label_ResID. Esse recurso é carregado da DLL satélite de VSPackage.  
  
 O **pasta** valor representa um GUID de uma pasta sob a qual o nó Folder_Label_ResID é exibido. No exemplo, o GUID representa o **outros projetos** pasta o **tipos de projeto** painel do **novo projeto** caixa de diálogo. Se o **outros projetos** valor estiver ausente, o rótulo é posicionado no nível superior.  
  
 O valor TemplatesDir Especifica o caminho completo do diretório que contém os modelos de projeto. Esses arquivos podem ser arquivos. vsz ou arquivos de modelo comum a ser clonado.  
  
 Se você especificar TemplatesLocalizedSubDir, ele deve ser a identificação de recurso de uma cadeia de caracteres que nomeia o subdiretório TemplatesDir que contém modelos localizados. Porque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de cadeia de caracteres de uma DLL satélite se você tiver um, cada DLL satélite pode conter um nome de subdiretório diferentes. O valor SortPriority Especifica uma prioridade de classificação.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Registrando o projeto e modelos de Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionando itens a adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionando pastas para a caixa de diálogo Novo Item adicionar](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
