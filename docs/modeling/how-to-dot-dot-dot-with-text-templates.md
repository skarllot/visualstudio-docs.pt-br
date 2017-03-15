---
title: Como com modelos de texto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>Como ... com modelos de texto
Modelos de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornecem uma maneira útil de geração de texto de qualquer tipo. Você pode usar modelos de texto para gerar o texto em tempo de execução como parte do seu aplicativo e em tempo de design para gerar alguns dos seus códigos de projeto. Este tópico resume a mais frequentes "Como faço..." perguntas.  
  
 Neste tópico, várias respostas que são precedidas por marcadores são sugestões alternativos.  
  
 Para obter uma introdução geral para modelos de texto, ler [de geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Como...  
  
### <a name="generate-part-of-my-application-code"></a>Gerar a parte do código do meu aplicativo  
 Tenho uma configuração ou *modelo* em um arquivo ou um banco de dados. Uma ou mais partes do meu código dependem do modelo.  
  
-   Gere alguns de seus arquivos de código a partir de modelos de texto. Para obter mais informações, consulte [geração de código de tempo de Design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e [o que é a melhor maneira de começar a escrever um modelo?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Gerar arquivos em tempo de execução, passando dados para o modelo  
 Em tempo de execução, o meu aplicativo gera arquivos de texto, como relatórios, que contêm uma mistura de texto padrão e dados. Desejo evitar a escrita de centenas de `write` instruções.  
  
-   Adicione um modelo de texto de tempo de execução ao seu projeto. Este modelo cria uma classe em seu código, que você pode criar uma instância e usar para gerar o texto. Você pode passar dados para ele nos parâmetros do construtor. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Se você quiser gerar a partir de modelos que estão disponíveis somente em tempo de execução, você pode usar modelos de texto padrão. Se você estiver escrevendo um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão, você pode chamar o serviço de modelagem de texto. Para obter mais informações, consulte [invocando transformação de texto em uma extensão VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). Em outros contextos, você pode usar o mecanismo de modelagem de texto. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     Use o \<#@parameter#> diretiva passar parâmetros para esses modelos. Para obter mais informações, consulte [diretiva de parâmetro T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Leia a outro arquivo de projeto de um modelo  
 Para ler um arquivo da mesma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto do modelo:  
  
-   Insira `hostSpecific="true"` na diretiva `<#@template#>`.  
  
     Em seu código, use `this.Host.ResolvePath(filename)` para obter o caminho completo do arquivo.  
  
### <a name="invoke-methods-from-a-template"></a>Chamar métodos de um modelo  
 Se os métodos já existirem, por exemplo, no padrão [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classes:  
  
-   Use o \<#@assembly#> diretiva para carregar o assembly e usar \<#@import#> para definir o contexto de namespace. Para obter mais informações, consulte [a diretiva de importação T4](../modeling/t4-import-directive.md).  
  
     Se você frequentemente usa o mesmo conjunto de assembly e importa diretivas, considere escrever um processador de diretriz. Em cada modelo, você pode chamar o processador de diretriz, que pode carregar os assemblies e os arquivos de modelo e definir o contexto de namespace. Para obter mais informações, consulte [criação personalizada T4 texto modelo diretiva processadores](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Se você estiver escrevendo os métodos:  
  
-   Se você estiver escrevendo um modelo de texto de tempo de execução, escreva uma definição de classe parcial que tenha o mesmo nome que o modelo de texto de tempo de execução. Adicione os métodos adicionais para essa classe.  
  
-   Gravar um bloco de controle de recurso de classe `<#+ ... #>` no qual você pode declarar métodos, propriedades e classes privadas. Quando o modelo de texto é compilado, ele é transformado em uma classe. Os blocos de controle padrão `<#...#>` e texto são transformados em um único método, e blocos de recurso de classe são inseridos como membros separados. Para obter mais informações, consulte [blocos de controle do modelo de texto](../modeling/text-template-control-blocks.md).  
  
     Métodos definidos como recursos de classe também podem incluir os blocos de texto incorporado.  
  
     Considere a colocação de recursos de classe em um arquivo separado que você pode `<#@include#>` em um ou mais arquivos de modelo.  
  
-   Os métodos de gravação em um assembly separado (biblioteca de classes) e chamá-los a partir do modelo. Use o `<#@assembly#>` diretiva para carregar o assembly e `<#@import#>` para definir o contexto de namespace. Observe que para recompilar o assembly enquanto ele está sendo depurado, você pode ter que interromper e reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Gerar muitos arquivos de esquema de um modelo  
 Se você geralmente pode gerar arquivos de modelos que têm o mesmo esquema XML ou banco de dados:  
  
-   Considere escrever um processador de diretriz. Isso permite que você substitua várias instruções de assembly e importar instruções em cada modelo com uma única diretiva personalizada. O processador de diretriz também pode carregar e analisar o arquivo de modelo. Para obter mais informações, consulte [criação personalizada T4 texto modelo diretiva processadores](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Gerar arquivos de um modelo complexo  
  
-   Considere a criação de uma linguagem específica do domínio (DSL) para representar o modelo. Isso torna muito mais fácil escrever modelos, porque você usa tipos e propriedades que refletem os nomes dos elementos em seu modelo. Não é preciso analisar o arquivo ou navegar em nós XML. Por exemplo:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Para obter mais informações, consulte [guia de Introdução com linguagens específicas de domínio](../modeling/getting-started-with-domain-specific-languages.md) e [código de geração de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Obter dados[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Para usar os serviços fornecidos na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por conjunto de `hostSpecific` atributo e carga o `EnvDTE` assembly. Por exemplo:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>Executar modelos de texto no processo de compilação  
  
-   Para obter mais informações, consulte [geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Perguntas gerais mais  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>O que é a melhor maneira de começar a escrever um modelo de texto?  
  
1.  Escreva um exemplo específico do arquivo gerado.  
  
2.  Transformá-lo em um modelo de texto inserindo o `<#@template #>` diretiva e as diretivas e código que são necessárias para carregar o arquivo de entrada ou modelo.  
  
3.  Substitua progressivamente partes do arquivo com a expressão e blocos de código.  
  
### <a name="what-is-a-model"></a>O que é um "modelo"?  
  
-   A entrada lida por seu modelo. É possível em um arquivo ou em um banco de dados. Pode ser XML, ou um desenho do Visio, ou uma linguagem específica do domínio (DSL) ou um modelo UML, ou pode ser texto sem formatação. Ele pode ser dividido em vários arquivos. Normalmente, mais de um modelo lê um modelo.  
  
     A implicação do termo "modelo" é que ele representa algum aspecto do seu negócio mais diretamente que o código de programa gerado ou outros arquivos. Por exemplo, ele pode representar o plano de uma rede de comunicações que seu software gerado será supervisionar.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Qual é a vantagem de usar modelos de texto?  
 Normalmente, você gerar vários código ou outros arquivos de um modelo. O modelo representa os requisitos mais diretamente o código gerado. Ele omite o detalhe de implementação e é gravado em termos de requisitos, em vez do código. Quando os requisitos são alterados – como normalmente o fazem – você pode atualizar o modelo mais fácil e mais confiável do que as diferentes partes do código do programa.  
  
 Geração de código, portanto, é uma ferramenta valiosa sob a perspectiva dos métodos de desenvolvimento ágeis.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Quais "práticas recomendadas" existem para modelos de texto?  
  
-   Para obter mais informações, consulte [diretrizes para modelos de texto T4 escrita](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>O que é "T4"?  
  
-   Outro nome para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recursos de modelo de texto descritos aqui. A versão anterior, que não foi publicada, foi uma abreviação de "Transformação de modelo de texto".

