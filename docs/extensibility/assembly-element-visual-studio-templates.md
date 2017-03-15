---
title: Elemento Assembly (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67e72cf79ad1191356342150f21f3b89fd7daeec
ms.lasthandoff: 02/22/2017

---
# <a name="assembly-element-visual-studio-templates"></a>Elemento de assembly (modelos do Visual Studio)
Especifica informações sobre um assembly, que usa o modelo para adicionar uma referência de assembly para projetos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Referências >  
 \<Referência >  
 \<Assembly >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Referência](../extensibility/reference-element-visual-studio-templates.md)|Especifica a referência de assembly para adicionar quando o item é adicionado a um projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse texto Especifica o assembly a ser adicionado a um projeto quando o modelo de item é instanciado. Esse nome de assembly deve ser especificado em uma das seguintes maneiras:  
  
-   Como um nome completo do assembly. Por exemplo:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Como referência de texto simples. Por exemplo:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Comentários  
 O `Assembly` é um elemento filho obrigatório de `Reference`.  
  
 O `Reference`, `References,` e `Assembly` elementos só podem ser usados em arquivos. vstemplate que têm um `Type` valor do atributo `Item`.  
  
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
