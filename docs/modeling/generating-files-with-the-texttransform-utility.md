---
title: "Gerando arquivos com o utilitário TextTransform | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
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
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>Gerando arquivos com o utilitário TextTransform
TextTransform.exe é uma ferramenta de linha de comando que você pode usar para transformar um modelo de texto. Quando você chama TextTransform.exe, você especifica o nome de um arquivo de modelo de texto como um argumento. TextTransform.exe chama o mecanismo de transformação de texto e processa o modelo de texto. TextTransform.exe geralmente é chamado de scripts. No entanto, não é geralmente necessário, porque você pode executar a transformação de texto no Visual Studio ou no processo de compilação.  
  
> [!NOTE]
>  Se você desejar executar a transformação de texto como parte de um processo de compilação, considere usar a tarefa de transformação de texto do MSBuild. Para obter mais informações, consulte [geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md). Em um computador em que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estiver instalado, você também pode escrever um aplicativo ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que pode transformar modelos de texto. Para obter mais informações, consulte [modelos de processamento de texto usando um Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe está localizado no seguinte diretório:  
  
 **\Program Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Sintaxe  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|**Argumento**|**Descrição**|  
|------------------|---------------------|  
|`templateName`|Identifica o nome do arquivo de modelo que você deseja transformar.|  
  
|**Opção**|**Descrição**|  
|----------------|---------------------|  
|**-out** \<filename >|O arquivo no qual a saída da transformação é gravada.|  
|**-r** \<assembly >|Um assembly usado para compilar e executar o modelo de texto.|  
|**-u** \<namespace >|Um namespace que é usado para compilar o modelo.|  
|**-I** \<includedirectory >|Um diretório que contém os modelos de texto incluídos no modelo de texto especificado.|  
|**-P** \<referencepath >|Um diretório para pesquisar assemblies especificados dentro do modelo de texto ou usando o **- r** opção.<br /><br /> Por exemplo, para incluir os assemblies usados para a API do Visual Studio, use<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\< nome da classe >! \<assemblyName | codeBase >|O nome, o nome completo do tipo e o assembly de um processador de diretriz que pode ser usado para processar as diretivas personalizadas dentro do modelo de texto.|  
|**-a** [processorName]! [ directiveName]! \<parameterName >! \<parameterValue >|Especifique um valor de parâmetro para um processador de diretriz. Se você especificar apenas o nome do parâmetro e o valor, o parâmetro estarão disponível para todos os processadores de diretriz. Se você especificar um processador de diretriz, o parâmetro está disponível somente para o processador especificado. Se você especificar um nome de diretiva, o parâmetro está disponível somente quando a diretiva especificada está sendo processada.<br /><br /> Para acessar os valores de parâmetro de um processador de diretriz ou modelo de texto, use <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> Em um modelo de texto incluem `hostspecific` na diretiva do modelo e invocar a mensagem em `this.Host`. Por exemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Digite sempre o '!' marca, mesmo se você omitir o processador opcional e nomes de diretiva. Por exemplo:<br /><br /> `-a !!param!value`|  
|**-h**|Fornece ajuda.|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Tarefa|Tópico|  
|----------|-----------|  
|Gerar arquivos em uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Grave processadores de diretivas para transformar suas próprias fontes de dados.|[Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)|  
|Escreva um host de modelagem de texto que permite que você invoque modelos de texto de seu próprio aplicativo.|[Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
