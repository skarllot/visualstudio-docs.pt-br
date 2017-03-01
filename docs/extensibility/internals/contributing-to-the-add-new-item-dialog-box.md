---
title: "Contribuindo para a caixa de diálogo Novo Item adicionar | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
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
ms.openlocfilehash: 29b4419c5fc76ffb4f8e17713c336c18c62654f8
ms.lasthandoff: 02/22/2017

---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Contribuindo para a caixa de diálogo Novo Item adicionar
Um subtipo de projeto pode fornecer um novo diretório completo de itens para o **Add New Item** caixa de diálogo Registrar **Adicionar Item** modelos sob o `Projects` subchave do registro.  
  
## <a name="registering-add-new-item-templates"></a>Registro de modelos para adicionar novo Item  
 Esta seção está localizada em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** no registro. As entradas do Registro abaixo pressupõem um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregadas por um subtipo de projeto hipotético. As entradas para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto estão listados abaixo.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 O `AddItemTemplates\TemplateDirs` subchave contém entradas de registro com o caminho para o diretório onde itens disponibilizados no **Adicionar Novo Item** caixa de diálogo são colocados.  
  
 O ambiente carrega automaticamente todos os `AddItemTemplates` dados sob o `Projects` subchave do registro. Isso pode incluir os dados para implementações de base do projeto, bem como os dados específicos subtipo para tipos de projeto. Subtipo de cada projeto é identificado por um tipo de projeto `GUID`. O subtipo de projeto pode especificar que uma alternativa conjunto de `Add Item` modelos devem ser usados para uma instância do tipo de projeto específico, oferecendo suporte a `VSHPROPID_ AddItemTemplatesGuid` enumeração de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>em <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>implementação para retornar o valor GUID do subtipo do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Se `VSHPROPID_AddItemTemplatesGuid` propriedade não for especificada, o projeto base GUID é usado.  
  
 Você pode filtrar itens no **Adicionar Novo Item** caixa de diálogo Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>interface no objeto projeto subtipo agregador.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Por exemplo, um subtipo de projeto que implementa um projeto de banco de dados agregando um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projeto, pode filtrar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] itens específicos do **Adicionar Novo Item** caixa de diálogo com a implementação de filtragem e em Ativar, poderá adicionar itens específicos do projeto de banco de dados, oferecendo suporte a `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Para obter mais informações sobre como filtrar e adicionar itens para o **Adicionar Novo Item** caixa de diálogo, consulte [a adição de itens para as caixas de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs para objetos que normalmente são usados para estender a projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
