---
title: "Referências de elemento (modelos do Visual Studio) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b5cd8ddd86c8a45ede87a35fc13fb064fa49ed83
ms.lasthandoff: 02/22/2017

---
# <a name="references-element-visual-studio-templates"></a>Elemento de referências (Modelos do Visual Studio)
Agrupa as referências de assembly que o modelo adiciona aos projetos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Referências >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Referência](../extensibility/reference-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Especifica a referência de assembly para adicionar quando o item é adicionado a um projeto. Deve haver um ou mais `Reference` elementos em um `References` elemento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica o conteúdo do modelo.|  
  
## <a name="remarks"></a>Comentários  
 O `References` é um elemento filho opcional de `TemplateContent`.  
  
 O `Reference` e `References` elementos podem ser usados somente em arquivos. vstemplate que têm um `Type` valor do atributo `Item`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o `TemplateContent` elemento de um modelo de item. Esse XML adiciona as referências aos assemblies System. dll e System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
