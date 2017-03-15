---
title: "T4 Diretiva de saída | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
author: alancameronwills
ms.author: awills
manager: douge
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
ms.openlocfilehash: a3062d101adc8cbd3f84c892cf1de26f7e16bac5
ms.lasthandoff: 02/22/2017

---
# <a name="t4-output-directive"></a>T4 Diretiva de saída
Em modelos de texto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a diretiva de `output` é usada pare definir a extensão do nome de arquivo e a codificação do arquivo transformado.  
  
 Por exemplo, se seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto inclui um arquivo de modelo chamado **MyTemplate.tt** que contém a seguinte diretiva:  
  
 `<#@output extension=".cs"#>`  
  
 em seguida, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] irá gerar um arquivo chamado **MyTemplate.cs**  
  
 A diretiva de `output` não é necessária em um modelo de texto de tempo de execução (pré-processado). Ao invés disso, o aplicativo obtém a cadeia de caracteres gerada ao chamar `TextTransform()`. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Usando a Diretiva de Saída  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Não deverá haver mais de uma diretiva de `output` em cada modelo de texto.  
  
## <a name="extension-attribute"></a>atributo de extensão  
 Especifica a extensão do nome de arquivo do arquivo de saída do texto gerado.  
  
 O valor padrão é **. cs**  
  
 Exemplos:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Valores aceitáveis:  
 Qualquer extensão de nome de arquivo válida.  
  
## <a name="encoding-attribute"></a>atributo de codificação  
 Especifica a codificação usada ao gerar o arquivo de saída. Por exemplo:  
  
 `<#@ output encoding="utf-8"#>`  
  
 O valor padrão é a codificação usada pelo arquivo de modelo de texto.  
  
 Valores aceitáveis:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (Padrão do sistema)  
  
 Em geral, você pode usar a cadeia de caracteres do WebName ou o número de página de código de qualquer uma das codificações retornadas pelo <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.</xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>
