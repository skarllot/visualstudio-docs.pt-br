---
title: Elemento RequiredPlatformVersion (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
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
ms.openlocfilehash: 77add1c081a630fa64e008707a20598d88c7fbe5
ms.lasthandoff: 02/22/2017

---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (Modelos do Visual Studio)
Especifica a versão mínima do sistema operacional que o modelo de projeto requer para funcionar corretamente. Esse elemento é usado para modelos de projeto que cria [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.  
  
 O `RequiredPlatformVersion` é comparado diretamente com a versão do sistema operacional. Se o `RequiredPlatformVersion` for maior do que a versão do sistema operacional, o modelo não aparecer no **novo projeto** caixa de diálogo. Para especificar um modelo para [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou superior, defina `RequiredPlatformVersion` para 6.2.0. Para especificar um modelo para [!INCLUDE[win81](../debugger/includes/win81_md.md)] ou superior, defina RequiredPlatformVersion para 6.3.0.  
  
 Modelos que especificam `RequiredPlatformVersion`=&8; são compatíveis com o cliente anterior [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modelos.  
  
 VSTemplate  
TemplateData  
….. TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 Nenhum.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica a plataforma que os destinos de modelo de projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
## <a name="remarks"></a>Comentários  
 Esse texto Especifica a versão mínima do sistema operacional necessária ao modelo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo especifica que as metas do projeto modelo [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou posterior.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento TargetPlatformName (modelos do Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Criando modelos de projeto e Item](../ide/creating-project-and-item-templates.md)   
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
