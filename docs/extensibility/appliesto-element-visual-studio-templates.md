---
title: Elemento AppliesTo (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 10
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
ms.openlocfilehash: e1114f171fc47f171b8b0243265bfa5693b8cafa
ms.lasthandoff: 02/22/2017

---
# <a name="appliesto-element-visual-studio-templates"></a>Elemento AppliesTo (modelos do Visual Studio)
Especifica uma expressão opcional para correspondência de um ou mais recursos. (see <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>).</xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> Recursos são expostos pelos tipos de projeto por meio da hierarquia como uma propriedade <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> Dessa maneira, o modelo pode ser compartilhado por vários tipos de projeto que têm recursos aplicáveis comuns.  
  
 Esse elemento é opcional. Pode haver um máximo de uma instância em um arquivo de modelo. Esse elemento permite que apenas um modelo de item seja aceito como aplicável, com base nos recursos do projeto ativo atualmente selecionado. Ele não pode ser usado para tornar um modelo de item não aplicável. Se `AppliesTo` estiver ausente ou a expressão não for aceita com sucesso, `TemplateID` ou `TemplateGroupID` serão usados para tornar o modelo aplicável, como nas versões anteriores do produto.  
  
 Introduzido no Visual Studio 2013 Atualização 2. Para fazer referência a versão correta, consulte [Referenciando Assemblies fornecidos no Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<AppliesTo >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<AppliesTo>Capability1</AppliesTo>   
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório. Esse texto especifica os recursos do projeto.  
  
 A sintaxe da expressão válida é definida como:  
  
-   A expressão de recurso, como "(VisualC | CSharp) + (MSTest | NUnit) ".  
  
-   O "|" é o operador OR.  
  
-   Os caracteres "&" e "+" são operadores AND.  
  
-   O caractere "!" é o operador NOT.  
  
-   Parênteses forçam a ordem de precedência de avaliação.  
  
-   Uma expressão nula ou vazia é avaliada como uma correspondência.  
  
-   Recursos de projeto podem ser qualquer caractere, exceto os caracteres reservados: "' :;,+-*/\\! ~ | < / % $@ ^ () = [] {}<>? \t\b\n\r  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra três modelos diferentes. `Template1` aplica-se a todos os tipos de projeto do C# ou a qualquer outro tipo de projeto que ofereça suporte ao recurso `WindowsAppContainer`. `Template2` aplica-se a todos os projetos do C# de qualquer tipo. `Template3` aplica-se aos projetos do C# que não são projetos `WindowsAppContainer`.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
