---
title: "Itens de projeto comuns do MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, itens de projeto comuns"
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Itens de projeto comuns do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], um item é uma referência nomeada a um ou mais arquivos.  Itens contêm metadados, como nomes de arquivos, caminhos e números de versão.  De tipos em todos os projetos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] têm vários itens em comum.  Esses itens são definidos no microsoft.build.commontypes.xsd arquivo.  
  
## Itens Comuns  
 A seguir é uma lista de todos os itens de projeto comum.  
  
### Referência  
 Representa uma referência de assembly \(gerenciado\) no projeto.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|HintPath|Cadeia de caracteres opcional.  Caminho relativo ou absoluto do assembly.|  
|Nome|Cadeia de caracteres opcional.  O nome para exibição do assembly, por exemplo, "System.Windows.Forms".|  
|FusionName|Cadeia de caracteres opcional.  Especifica o nome de fusão simples ou forte para o item.<br /><br /> Quando esse atributo estiver presente, isso pode economizar tempo porque o arquivo de assembly não precisa ser aberto para obter o nome de fusão.|  
|SpecificVersion|Booleano opcional.  Especifica se apenas a versão no nome de fusão deve ser referenciada.|  
|Aliases|Cadeia de caracteres opcional.  Nenhum alias para a referência.|  
|Particular|Booleano opcional.  Especifica se a referência deve ser copiada para a pasta de saída.  Esse atributo corresponde a **Copy Local** propriedade de referência que está no IDE do Visual Studio.|  
  
### COMReference  
 Representa um componente \(não gerenciado\) COM referência no projeto.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|Nome|Cadeia de caracteres opcional.  O nome de exibição do componente.|  
|GUID|Cadeia de caracteres opcional.  Um GUID para o componente, no formato {12345678\-1234\-1234\-1234\-1234567891234}.|  
|VersionMajor|Cadeia de caracteres opcional.  A parte principal do número de versão do componente.  Por exemplo, "5" se o número de versão completa é "5.46".|  
|VersionMinor|Cadeia de caracteres opcional.  A parte secundária do número de versão do componente.  Por exemplo, "46" se o número de versão completa é "5.46".|  
|LCID|Cadeia de caracteres opcional.  A identificação de localidade para o componente.|  
|WrapperTool|Cadeia de caracteres opcional.  O nome da ferramenta wrapper que é usado no componente, por exemplo, "tlbimp".|  
|Isolada|Booleano opcional.  Especifica se o componente é um componente com sem registro.|  
  
### COMFileReference  
 Representa uma lista de bibliotecas de tipos que alimentam o destino ResolvedComreference.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|WrapperTool|Cadeia de caracteres opcional.  O nome da ferramenta wrapper que é usado no componente, por exemplo, "tlbimp".|  
  
### NativeReference  
 Representa um arquivo de manifesto nativo ou uma referência a esse arquivo.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|Nome|Cadeia de caracteres obrigatória.  O nome base do arquivo de manifesto.|  
|HintPath|Cadeia de caracteres obrigatória.  O caminho relativo do arquivo de manifesto.|  
  
### ProjectReference  
 Representa uma referência a outro projeto.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|Nome|Cadeia de caracteres opcional.  O nome de exibição da referência.|  
|Projeto|Cadeia de caracteres opcional.  Um GUID para a referência, na forma {12345678\-1234\-1234\-1234\-1234567891234}.|  
|Pacote|Cadeia de caracteres opcional.  O caminho do arquivo de projeto que está sendo referenciado.|  
  
### Compilar  
 Representa os arquivos de origem para o compilador.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|DependentUpon|Cadeia de caracteres opcional.  Especifica o arquivo que desse arquivo depende para compilar corretamente.|  
|AutoGen|Booleano opcional.  Indica se o arquivo foi gerado para o projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\).|  
|Link|Cadeia de caracteres opcional.  O notação caminho a ser exibida quando o arquivo estiver localizado fisicamente fora a influência do arquivo do projeto.|  
|Visível|Booleano opcional.  Indica se deve exibir o arquivo em **Solution Explorer** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Cadeia de caracteres opcional.  Determina se deve copiar o arquivo para o diretório de saída.  Os valores são:<br /><br /> 1.  Nunca<br />2.  Sempre<br />3.  PreserveNewest|  
  
### EmbeddedResource  
 Representa os recursos a serem incorporados no assembly gerado.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|DependentUpon|Cadeia de caracteres opcional.  Especifica o arquivo que desse arquivo depende para compilar corretamente|  
|Gerador|Cadeia de caracteres obrigatória.  O nome de um gerador de arquivo executado neste item.|  
|LastGenOutput|Cadeia de caracteres obrigatória.  O nome do arquivo que foi criado por um gerador de arquivo executado neste item.|  
|CustomToolNamespace|Cadeia de caracteres obrigatória.  O namespace no qual qualquer arquivo gerador executado neste item deve criar código.|  
|Link|Cadeia de caracteres opcional.  O caminho de notação é exibido se o arquivo estiver localizado fisicamente fora a influência do projeto.|  
|Visível|Booleano opcional.  Indica se deve exibir o arquivo em **Solution Explorer** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Cadeia de caracteres opcional.  Determina se deve copiar o arquivo para o diretório de saída.  Os valores são:<br /><br /> 1.  Nunca<br />2.  Sempre<br />3.  PreserveNewest|  
|LogicalName|Cadeia de caracteres obrigatória.  O nome lógico do recurso inserido.|  
  
### Conteúdo  
 Representa os arquivos que não são compilados no projeto, mas podem ser incorporados ou publicados com ele.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|DependentUpon|Cadeia de caracteres opcional.  Especifica o arquivo que desse arquivo depende para compilar corretamente.|  
|Gerador|Cadeia de caracteres obrigatória.  O nome de um gerador de arquivo executado neste item.|  
|LastGenOutput|Cadeia de caracteres obrigatória.  O nome do arquivo que foi criado por um gerador de arquivo que foi executado neste item.|  
|CustomToolNamespace|Cadeia de caracteres obrigatória.  O namespace no qual qualquer arquivo gerador executado neste item deve criar código.|  
|Link|Booleano opcional.  Indica se deve exibir o arquivo em **Solution Explorer** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|PublishState|Cadeia de caracteres obrigatória.  O estado de publicação de conteúdo, ambos:<br /><br /> -   Padrão<br />-   Incluído<br />-   Excluído<br />-   Arquivo de dados<br />-   Pré\-requisito|  
|IsAssembly|Booleano opcional.  Especifica se o arquivo é um assembly.|  
|Visível|Booleano opcional.  Indica se deve exibir o arquivo em **Solution Explorer** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Cadeia de caracteres opcional.  Determina se deve copiar o arquivo para o diretório de saída.  Os valores são:<br /><br /> 1.  Nunca<br />2.  Sempre<br />3.  PreserveNewest|  
  
### Nenhum  
 Representa os arquivos que devem ter função no processo de compilação.  
  
|Nome do Item|Descrição|  
|------------------|---------------|  
|DependentUpon|Cadeia de caracteres opcional.  Especifica o arquivo que desse arquivo depende para compilar corretamente.|  
|Gerador|Cadeia de caracteres obrigatória.  O nome de um gerador de arquivo executado neste item.|  
|LastGenOutput|Cadeia de caracteres obrigatória.  O nome do arquivo que foi criado por um gerador de arquivo executado neste item.|  
|CustomToolNamespace|Cadeia de caracteres obrigatória.  O namespace no qual qualquer arquivo gerador executado neste item deve criar código.|  
|Link|Cadeia de caracteres opcional.  O notação caminho a ser exibido se o arquivo estiver localizado fisicamente fora a influência do projeto.|  
|Visível|Booleano opcional.  Indica se deve exibir o arquivo em **Solution Explorer** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Cadeia de caracteres opcional.  Determina se deve copiar o arquivo para o diretório de saída.  Os valores são:<br /><br /> 1.  Nunca<br />2.  Sempre<br />3.  PreserveNewest|  
  
### BaseApplicationManifest  
 Representa o manifesto do aplicativo base para compilação e contém [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] informações de segurança de implantação.  
  
### CodeAnalysisImport  
 Representa o projeto do FxCop para importar.  
  
### Importar  
 Representa os assemblies cujos namespaces devem ser importados pelo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador.  
  
## Consulte também  
 [Propriedades de projeto comuns do MSBuild](../msbuild/common-msbuild-project-properties.md)