---
title: "Suporte para configurações do usuário | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
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
ms.openlocfilehash: f33788559a3c36cb2929795e67dfba8dbdf90539
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-user-settings"></a>Suporte para configurações de usuário
Um VSPackage pode definir uma ou mais categorias de configurações, que são grupos de variáveis de estado que persistem quando um usuário escolhe o **configurações de importação/exportação** comando o **ferramentas** menu. Para habilitar essa persistência, use as APIs de configurações no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Uma entrada de registro que é conhecida como um ponto de configurações personalizado e um GUID define a categoria de configurações do VSPackage. Um VSPackage pode oferecer suporte a várias categorias de configurações, definidos por um ponto de configurações personalizado.  
  
-   Implementações de configurações que se baseiam em assemblies de interoperabilidade (usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>interface) deve criar o ponto de configurações personalizado a edição do registro ou usando um script de registrador (arquivo RGS).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Para obter mais informações, consulte [criação de Scripts do registrador](/visual-cpp/atl/creating-registrar-scripts).  
  
-   O código que usa a estrutura de pacote gerenciado (MPF) deve criar pontos de configurações personalizado anexando um <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>para o VSPackage para cada ponto de configurações personalizado.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
     Se um único VSPackage oferece suporte a vários pontos de configurações personalizadas, cada ponto de configurações personalizado é implementado por uma classe separada, e cada um deles é registrado por uma instância única da <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>classe.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Consequentemente, as configurações de implementação de classe podem oferecer suporte a mais de uma categoria de configurações.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Detalhes da entrada do registro ponto configurações personalizadas  
 Pontos de configurações personalizadas são criados em uma entrada de registro no seguinte local: HKLM\Software\Microsoft\VisualStudio\\*\<versão >*\UserSettings\\`<CSPName>`, onde `<CSPName>` é o nome do ponto de configurações personalizado suporta o VSPackage e * \<versão >* é a versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por exemplo 8.0.  
  
> [!NOTE]
>  O caminho raiz do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* pode ser substituído por uma alternativa raiz quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) é inicializado. Para obter mais informações, consulte [opções de linha de comando](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 A estrutura da entrada do registro é ilustrada abaixo:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<versão >*\UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 Pacote = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Categoria = '{aaaa AAAAAA aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = CategoryName  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|(Padrão)|REG_SZ|Nome do ponto de configurações personalizadas|O nome da chave, `<CSPName`>, é o nome do ponto de configurações personalizado não localizado.<br /><br /> Para implementações baseadas em MPF, o nome da chave é obtido pela combinação de `categoryName` e `objectName` argumentos a <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>construtor em `categoryName_objectName`.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute><br /><br /> A chave pode ser vazia ou pode conter a ID de referência para a cadeia de caracteres em uma DLL satélite localizada. Esse valor é obtido o `objectNameResourceID` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>construtor.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Pacote|REG_SZ|GUID|O GUID do VSPackage que implementa o ponto de configurações personalizado.<br /><br /> Implementações com base em MPF usando o <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>da classe, use o construtor `objectType` argumento contendo o VSPackage <xref:System.Type>e reflexão para obter esse valor.</xref:System.Type> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Categoria|REG_SZ|GUID|GUID que identifica a categoria de configurações.<br /><br /> Para implementações baseadas em assemblies de interoperabilidade, esse valor pode ser um escolhido arbitrariamente GUID, que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passa para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> Todas as implementações desses dois métodos devem verificar seus argumentos GUID.<br /><br /> Para implementações baseadas em MPF, esse GUID é obtida pelo <xref:System.Type>da classe implementando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo configurações.</xref:System.Type>|  
|ResourcePackage|REG_SZ|GUID|Opcional.<br /><br /> Caminho para a DLL contendo de satélite localizada cadeias de caracteres se VSPackage implementação não fornecê-las.<br /><br /> MPF usa a reflexão para obter o recurso correto VSPackage, portanto, a <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>classe não definir esse argumento.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|AlternateParent|REG_SZ|Nome da pasta na página de opções de ferramentas que contém esse ponto de configurações personalizado.|Opcional.<br /><br /> Você deve definir esse valor somente se dá suporte a uma implementação de configurações **opções de ferramentas** páginas que usam o mecanismo de persistência no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] em vez do mecanismo no modelo de automação para salvar o estado.<br /><br /> Nesses casos, o valor na chave AlternateParent é o `topic` seção o `topic.sub-topic` cadeia de caracteres usada para identificar determinado **ToolsOptions** página. Por exemplo, para o **ToolsOptions** página `"TextEditor.Basic"` o valor de AlternateParent seria `"TextEditor"`.<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>gera o ponto de configurações personalizado, ele é o mesmo que o nome da categoria.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|
