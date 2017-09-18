---
title: "Opções e páginas de opções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
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
ms.openlocfilehash: c13b562fd263bf2ccc71af30634be8cd9278593c
ms.lasthandoff: 02/22/2017

---
# <a name="options-and-options-pages"></a>Opções e páginas de opções
Clicando em **opções** sobre o **ferramentas** menu abre o **opções** caixa de diálogo. As opções nessa caixa de diálogo são coletivamente chamadas de páginas de opções. O controle de árvore no painel de navegação inclui opções categorias e cada categoria tem páginas de opções. Quando você seleciona uma página, suas opções são exibidas no painel à direita. Essas páginas permitem que você altere os valores das opções que determinam o estado de um VSPackage.  
  
## <a name="support-for-options-pages"></a>Suporte para páginas de opções  
 O <xref:Microsoft.VisualStudio.Shell.Package>classe oferece suporte para a criação de páginas de opções e categorias de opções.</xref:Microsoft.VisualStudio.Shell.Package> O <xref:Microsoft.VisualStudio.Shell.DialogPage>classe implementa uma página de opções.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage>oferece suas propriedades públicas para um usuário em uma grade genérica de propriedades.</xref:Microsoft.VisualStudio.Shell.DialogPage> Você pode personalizar esse comportamento, substituindo vários métodos na página para criar uma página de opções personalizadas que tem sua própria interface de usuário (UI). Para obter mais informações, consulte [criar uma página de opções](../../extensibility/creating-an-options-page.md).  
  
 O <xref:Microsoft.VisualStudio.Shell.DialogPage>classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que fornece a persistência de páginas de opções e configurações do usuário.</xref:Microsoft.VisualStudio.Shell.IProfileManager> </xref:Microsoft.VisualStudio.Shell.DialogPage> As implementações padrão da <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>métodos manter as alterações de propriedade em uma seção do registro de usuário se a propriedade pode ser convertida em uma cadeia de caracteres.</xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> </xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>  
  
## <a name="options-page-registry-path"></a>Caminho de registro da página de opções  
 Por padrão, o caminho do registro das propriedades gerenciadas por uma página de opções é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, o word DialogPage e o nome do tipo das opções de classe de página</xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> Por exemplo, uma classe de página de opções pode ser definida da seguinte maneira.  
  
 [!code-cs[&#1; VSSDKSupportForOptionsPages](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs) ] 
 [!code-vb [VSSDKSupportForOptionsPages n º&1;](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Se a <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>for HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, então os pares de nome e valor de propriedade são subchaves do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.</xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
  
 O caminho do registro da própria página de opções é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, o word, ToolsOptionsPages e as opções da página categoria e nome.</xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> Por exemplo, se a página de opções personalizada tem a categoria, minhas páginas de opção e o <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>é HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, em seguida, a página de opções tem a chave do registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My opção Pages\Custom.</xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Ferramentas/opções de Layout e os atributos de página  
 O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>atributo determina o agrupamento de páginas de opções personalizadas em categorias na árvore de navegação do **opções** caixa de diálogo.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> O <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>atributo associa uma página de opções de VSPackage que fornece a interface.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Considere o fragmento de código a seguir:  
  
 [!code-cs[N º&2; VSSDKSupportForOptionsPages](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs) ] 
 [!code-vb [VSSDKSupportForOptionsPages n º&2;](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Isso declara MyPackage fornece duas páginas de opções, OptionsPageGeneral e OptionsPageCustom. No **opções** caixa de diálogo, ambas as páginas de opções aparecem no **minhas páginas de opção** categoria como **geral** e **personalizado**, respectivamente.  
  
## <a name="option-attributes-and-layout"></a>Atributos de opção e Layout  
 A interface do usuário (IU) que fornece a página determina a aparência das opções em uma página de opções personalizadas. O layout, identificando e descrição das opções em uma página de opções genéricas são determinados pelos seguintes atributos:  
  
-   <xref:System.ComponentModel.CategoryAttribute>Determina a categoria da opção.</xref:System.ComponentModel.CategoryAttribute>  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>Determina o nome de exibição da opção.</xref:System.ComponentModel.DisplayNameAttribute>  
  
-   <xref:System.ComponentModel.DescriptionAttribute>Determina a descrição da opção.</xref:System.ComponentModel.DescriptionAttribute>  
  
    > [!NOTE]
    >  Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usar os recursos de cadeia de caracteres para localização e são definidos no [exemplo projeto gerenciado](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Considere o fragmento de código a seguir:  
  
 [!code-cs[N º&3; VSSDKSupportForOptionsPages](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages n º&3;](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 A opção OptionInteger aparece na página de opções como **opção inteiro** no **minhas opções** categoria. Se a opção for selecionada, a descrição, **minha opção inteiro**, é exibida na caixa de descrição.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Acessando páginas de opções de VSPackage outro  
 Um VSPackage que hospeda e gerencia uma página de opções pode ser acessado programaticamente de VSPackage outro usando o modelo de automação. Por exemplo, no código a seguir um VSPackage é registrado como uma página de opção de hospedagem.  
  
 [!code-cs[N º&4; VSSDKSupportForOptionsPages](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs) ] 
 [!code-vb [VSSDKSupportForOptionsPages n º&4;](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 O fragmento de código a seguir obtém o valor de OptionInteger de MyOptionPage:  
  
 [!code-cs[N º&5; VSSDKSupportForOptionsPages](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs) ] 
 [!code-vb [VSSDKSupportForOptionsPages n º&5;](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Quando o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>atributo registra uma página de opções, a página é registrada com a tecla se AutomationProperties o `SupportsAutomation` argumento do atributo é `true`.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Automação examina esta entrada do registro para encontrar o VSPackage associado e a automação e acessa a propriedade através da página de opções hospedado, neste caso, minha página de grade.  
  
 O caminho do registro da propriedade de automação é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, o word, AutomationProperties e as opções da página categoria e nome.</xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> Por exemplo, se a página de opções tem a categoria My Category, o nome de minha página de grade e o <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp e, em seguida, a propriedade de automação tem a chave do registro, a página de grade Category\My HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.</xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
  
> [!NOTE]
>  O nome canônico, minha página de grade Category.My, é o valor da subchave do nome dessa chave.
