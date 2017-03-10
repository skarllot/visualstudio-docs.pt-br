---
title: "Usando p&#225;ginas de op&#231;&#245;es | Microsoft Docs"
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
  - "Páginas de opções [Visual Studio SDK], uso de ferramentas"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# Usando p&#225;ginas de op&#231;&#245;es
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece o modelo de automação a <xref:EnvDTE.DTE> para habilitar os VSPackages acessar o **opções** na caixa de diálogo de **ferramentas** menu.  
  
 Normalmente, páginas de **opções** caixa de diálogo pode ser acessada usando o modelo de automação, se as páginas são fornecidas pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\) ou por um VSPackage. No entanto, há algumas exceções, como segue:  
  
-   As configurações do **Ajuda dinâmica** página não pode ser acessada por meio de programação. O **Ajuda dinâmica** recurso pode ser controlado usando o modelo de automação, mas o controle deve ser feito diretamente no código. Para obter mais informações, consulte [How to: Control the Dynamic Help Window](http://msdn.microsoft.com/pt-br/7f5777aa-c270-4058-a175-8ce8a4ed25eb).  
  
-   Controle o **fontes e cores** configurações de página é fornecido por meio de sua própria API, não por meio do modelo de automação. Para obter mais informações, consulte [Usando fontes e cores](../extensibility/using-fonts-and-colors.md).  
  
-   Propriedades específicas de idioma não podem ser obtidas por meio do modelo de automação.  
  
 **Opções** páginas que não dão suporte a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de automação pode não retornar uma automação <xref:EnvDTE.Properties> coleção quando consultado. Se a coleção é retornada, nem todos os recursos estão presentes. Para obter informações sobre como gerenciar esses recursos, consulte [DTE Properties Collections](../Topic/DTE%20Properties%20Collections.md).  
  
## Gerenciar páginas de opções  
 Gerenciar **opções** páginas, um VSPackage deve obter um <xref:EnvDTE.DTE> objeto do modelo de automação.  
  
> [!NOTE]
>  Quando um VSPackage usa o modelo de automação para consulta e alterar configurações no instalado **opções** páginas, não estende a funcionalidade do IDE. Portanto, o pacote não precisa implementar um objeto de automação.  
  
 Para obter uma <xref:EnvDTE.DTE> objeto por meio do modelo de automação, chamada de <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> método e fornecer um argumento de ID de serviço do `SID_SDTE` e um argumento de interface de `IID__DTE`, da seguinte maneira.  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 Para obter uma <xref:EnvDTE.DTE> objeto usando o gerenciado pacote Framework \(MPF\), chamada de <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método e fornecer um `serviceType` parâmetro do tipo <xref:Microsoft.VisualStudio.Shell.Interop.SDTE>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 Um **opções** página especificada por dois identificadores. O primeiro identificador é uma cadeia de caracteres que indica a pasta que contém o **opções** página. O segundo identificador é uma cadeia de caracteres que indica o item específico nessa pasta. Elas são chamadas de um **opções** página de categoria e subcategoria, ou o tópico e subtópico.  
  
 Por exemplo, as configurações do editor de texto para manipular o código básico estão no painel de navegação, como o **básica** membro o **Editor de texto** pasta. O identificador para a categoria é `TextEditor` e sua subcategoria é `Basic`, e o **opções** página propriamente dita é conhecida como o `TextEditor.Basic` página.  
  
> [!NOTE]
>  Para localização e outros motivos, os nomes são exibidos no **opções** páginas podem diferir as cadeias de caracteres usadas como identificadores de categoria e subcategoria. Você terá que usar a automação para consultar o IDE para obter os identificadores corretos, se eles não estão documentados em outro lugar. O local do registro é HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versão VS \>*\\AutomationProperties, onde *\< versão VS \>* é o número de versão da versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [Registrando páginas de opções personalizadas](../misc/registering-custom-options-pages.md).  
  
 Você pode obter as propriedades para o `TextEditor.Basic` página por meio do modelo de automação usando o exemplo a seguir.  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 Para obter as propriedades usando o MPF, use o <xref:EnvDTE._DTE.Properties%2A> método.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 O <xref:EnvDTE.Properties.Item%2A> método retorna as configurações individuais do <xref:EnvDTE.Properties> coleção como uma <xref:EnvDTE.Property> objeto.  
  
 Assim como acontece com categorias e subcategorias, cada configuração tem um identificador que é uma cadeia de caracteres exclusiva. Por exemplo, o **tamanho da tabulação** definição no `TextEditor.Basic` página é identificada pela cadeia de caracteres, `TabSize`.  
  
> [!NOTE]
>  Para localização e outros motivos, os nomes são exibidos no **opções** páginas podem diferir as cadeias de caracteres usadas como identificadores de configuração. Você terá que usar a automação para consultar o IDE para obter os identificadores corretos, se eles não estão documentados em outro lugar.  
  
 Você pode usar o <xref:EnvDTE.Property.Value%2A> do <xref:EnvDTE.Property> objeto que é retornado pelo <xref:EnvDTE.Properties.Item%2A> método o <xref:EnvDTE.Properties> coleção para consultar e alterar o estado de configurações.  
  
 Por exemplo, para definir o **tamanho da tabulação** definição no `TextEditor.Basic` página através do modelo de automação, use o <xref:EnvDTE.Properties> objeto retornado no exemplo a seguir.  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 O exemplo a seguir demonstra como atualizar o **tamanho da tabulação** configuração usando o MPF.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 Para obter mais informações, consulte [Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md).  
  
## Persistindo configurações de página de opções  
 O IDE implementa a persistência de estado de **opções** páginas que dão suporte total a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de automação.  
  
 As configurações nas páginas que são incluídas no IDE são automaticamente salvas \(ou recuperadas\) quando um usuário clica o **configurações de importação\/exportação** comando o **ferramentas** menu.  
  
 Você pode habilitar seu personalizado **opções** página para usar esse suporte de persistência automática adicionando o `ProfileSave` Sinalizador personalizado **opções** página de entrada de registro em HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versão VS \>*\\AutomationProperties, onde *\< versão VS \>* é o número de versão da versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [Registrando páginas de opções personalizadas](../misc/registering-custom-options-pages.md).  
  
## Consulte também  
 [Criando páginas de opções usando Assemblies de interoperabilidade](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Criando páginas de opções](../extensibility/internals/creating-options-pages.md)   
 [Criando páginas de opções usando a automação](../misc/creating-options-pages-by-using-automation.md)   
 [Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md)   
 [Registrando páginas de opções personalizadas](../misc/registering-custom-options-pages.md)   
 [Abrir uma página de opções](../misc/opening-an-options-page.md)   
 [Opções e configurações de usuário estendendo](../extensibility/extending-user-settings-and-options.md)