---
title: "Suporte para categorias de configura&#231;&#245;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurações com suporte com o SDK do Visual Studio"
  - "SDK do Visual Studio, as configurações de suporte"
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Suporte para categorias de configura&#231;&#245;es
Uma categoria de configuração consiste em um grupo de opções que personalizam o ambiente de desenvolvimento integrado \(IDE\). Por exemplo, as configurações podem controlar o layout de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] windows e o conteúdo dos menus. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Sobre o **ferramentas** menu clique em **Import and Export Settings** para iniciar o **Import and Export Settings Wizard**. O assistente oferece três opções: exportar, importar ou redefinir as configurações. Por exemplo, selecionando export, abre o **Escolher configurações de exportação** página do assistente.  
  
 O controle de árvore no painel de navegação dessa página lista as categorias. Uma categoria é um grupo de configurações relacionadas que aparecem como um "ponto de configurações personalizadas", ou seja, como uma caixa de seleção. Você pode usar essas caixas de seleção para selecionar as categorias que deseja manter em um arquivo .vsettings. O assistente permite que você nomeie o arquivo .vsettings e especifique seu caminho.  
  
> [!NOTE]
>  Configurações salvos ou restauradas como uma categoria e nomes de configuração individuais não são exibidos no assistente.  
  
 A estrutura de pacote gerenciado \(MPF\) oferece suporte a criação de categorias de configurações com um mínimo de código adicional.  
  
-   Criar um VSPackage para fornecer um contêiner para a categoria ao subclassificar a <xref:Microsoft.VisualStudio.Shell.Package> classe.  
  
-   Criar a categoria em si, derivando\-na <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.  
  
-   Você conectá\-los com o <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Suporte para categorias de configurações  
 O <xref:Microsoft.VisualStudio.Shell.Package> classe oferece suporte para a criação de categorias. O <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa uma categoria. A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suas propriedades públicas para um usuário como uma categoria. Para obter mais informações, consulte [Criar uma categoria de configurações](../extensibility/creating-a-settings-category.md).  
  
 O <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, que fornece a persistência para páginas de opções e configurações do usuário. O <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> métodos persistirem configurações em um vssettings arquivo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, respectivamente. O <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> método redefine as configurações para seus valores padrão.  
  
 O <xref:Microsoft.VisualStudio.Shell.DialogPage> classe fornece uma implementação do <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> método que lê os pares nome\-valor do xml de feed e usa reflexão para descobrir as propriedades públicas no <xref:Microsoft.VisualStudio.Shell.DialogPage> classe derivada. Propriedades que têm nomes que coincidem com os pares nome\-valor são fornecidas valores correspondentes.  
  
 A implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> usa a reflexão para descobrir as propriedades públicas de <xref:Microsoft.VisualStudio.Shell.DialogPage> classe derivada e grava os valores e nomes de propriedade no feed XML como pares nome\-valor.  
  
### Caminho do registro de categoria de configurações  
 O caminho do registro da categoria de configurações é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, o word, UserSettings, a categoria de configurações e o nome do ponto de configurações personalizadas. Os nomes da categoria de configurações e configurações personalizadas de ponto são Unidos e separados por um sublinhado para formar o nome canônico, não traduzido que aparece no registro. Por exemplo, se a categoria de configurações é "My Category", as configurações personalizadas do ponto de nome "My Settings" e o ApplicationRegistryRoot HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, a categoria de configurações tem a chave do registro, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\UserSettings\\My Category\_My configurações.  
  
> [!NOTE]
>  O nome canônico não aparece em uma interface de usuário \(UI\). Ele é usado para associar um nome legível com a categoria de configurações, bem como um identificador programático \(ProgID\).  
  
### Atributo de categoria de configurações  
 O <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> determina o mapeamento das categorias para pontos de configurações personalizadas do **Import and Export Settings Wizard** associando o VSPackage que forneça uma categoria. Considere o fragmento de código a seguir:  
  
 [!code-vb[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/VisualBasic/support-for-settings-categories_1.vb)]
 [!code-cs[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/CSharp/support-for-settings-categories_1.cs)]  
  
 ID do recurso 106 mapeada "My Category", 107 para "My Settings" e 108 "Várias opções". Isso declara que `MyPackage` fornece a categoria, minhas configurações de Category\_My. A categoria é fornecida pelo `OptionsPageGeneral` classe, que deve implementar <xref:Microsoft.VisualStudio.Shell.IProfileManager>. As configurações dessa categoria são as propriedades públicas do `OptionsPageGeneral` classe.  
  
 No **Import and Export Settings Wizard**, o ponto de configurações com o nome, minhas configurações. Quando o ponto de configurações é selecionado, a descrição, **várias opções**, é exibida. O nome do ponto de configurações e a descrição são tiradas recursos de cadeia de caracteres localizada.  
  
## Consulte também  
 [Criando uma página de opções](../extensibility/creating-an-options-page.md)   
 [Exemplos VSSDK](../misc/vssdk-samples.md)   
 [Estado de VSPackage](/visual-cpp/misc/vspackage-state)   
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3)