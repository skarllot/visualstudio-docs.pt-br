---
title: "Registrando p&#225;ginas de op&#231;&#245;es personalizadas | Microsoft Docs"
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
  - "Registro, páginas de opções de ferramentas personalizadas"
  - "Páginas de opções de ferramentas [Visual Studio SDK], registrando"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# Registrando p&#225;ginas de op&#231;&#245;es personalizadas
Para um  **Opções de ferramentas** de página disponíveis para usuários e suporte a automação, deve ser registrado corretamente com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\).  
  
 **Ferramentas Opções** páginas com base na estrutura de pacote gerenciado registradas aplicando uma instância de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para o VSPackage fornecendo a página.  Suporte de automação é indicada pela configuração de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> propriedade `true`.  
  
## Registro de página de opções de ferramentas  
 Integrando um personalizado  **Ferramentas Opções** página com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] exige a criação de uma entrada do registro no seguinte local: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages, onde  *\<Version\>* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo 8.0.  
  
 A entrada possui uma chave primária com a categoria \(`<PageCategory>`\) do  **Ferramentas Opções** página e uma subchave que contém o nome da Subcategoria da página \(`<PageSubCategory>`\).  
  
 Por exemplo, o  **Ferramentas Opções** página identificada com a seqüência  **TextEditor.Basic**, tem uma chave do registro `<PageCategory>`\= textEditor com uma subchave de `<PageSubCategory>`\= Basic.  
  
 A estrutura da entrada do registro está abaixo:  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\  
  
 `<PageCategory>` \= '\#12345'  
  
 Pacote \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 ResourcePackage \= '{YYYYYY aaaa aaaa aaaa YYYYYYYYY}'  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 Página \= '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 Pacote \= '{AAAAAA AAAA AAAA AAAA AAAAAAAAA}'  
  
 ResourcePackage \= '{BBBBBB BBBB BBBB BBBB BBBBBBBBB}'  
  
 NoShowAllView \= 0\/1  
  
 A tabela a seguir lista os valores de HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|-----------|---------------|  
|\(Padrão\)|REG\_SZ|O nome canônico de categoria de personalizado  **Ferramentas Opções** página|O nome da chave, `<PageCategory>`, é o nome canônico de categoria não localizada do  **Ferramentas Opções** página. **Note:**  Se houver suporte para automação, os nomes canônicos de categoria e subcategoria não traduzidos são usados para obter um  **Ferramentas Opções** da página <xref:EnvDTE.Properties> coleção.  Para mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md). <br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, `<PageCategory`\> é obtida a partir de `categoryName` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.<br /><br /> A chave pode estar vazia ou pode conter a identificação de referência para a seqüência localizada na DLL de satélite da implementação.<br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, esse valor é obtido do `categoryResourceID` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.|  
|Pacote|REG\_SZ|GUID|O GUID do VSPackage implementando personalizado  **Ferramentas Opções** página.<br /><br /> Implementações baseiam a estrutura de pacote gerenciado usando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usar a reflexão para obter esse valor.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Uma DLL de satélite contendo localizadas strings se VSPackage implementação não fornecê\-las.<br /><br /> Estrutura gerenciada pacote usa a reflexão para obter o pacote de recursos correto para <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> não definir esse argumento.|  
  
 A tabela a seguir lista os valores de HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`\\`<PageSubCategory>`.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|-----------|---------------|  
|\(Padrão\)|REG\_SZ|O nome canônico subcategoria do custom  **Ferramentas Opções** página|O nome da chave, `<PageSubCategory`\>, é o nome canônico não localizada do  **Ferramentas Opções** subcategoria de página. **Note:**  Se houver suporte para automação, os nomes canônicos de categoria e subcategoria não traduzidos são usados para obter um  **Ferramentas Opções** da página <xref:EnvDTE.Properties> coleção.  Para mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md). <br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, `<PageSubegory`\> é obtida a partir de `pageName` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.<br /><br /> A chave pode estar vazia ou pode conter a identificação de referência para a seqüência localizada em uma DLL de uma implementação de satélite.<br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, esse valor é obtido do `pageNameResourceID` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.|  
|Página|REG\_SZ|GUID|O GUID do objeto de implementação personalizada  **Ferramentas Opções** página.<br /><br /> Implementações baseiam a estrutura de pacote gerenciado usando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usar o construtor `pageType` argumento contendo o VSPackage <xref:System.Type> e reflexão para obter esse valor.|  
|Pacote|REG\_SZ|GUID|Implementações baseiam a estrutura de pacote gerenciado usando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usar a reflexão para obter esse valor.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Uma DLL de satélite contendo localizadas strings se VSPackage implementação não fornecê\-las.<br /><br /> Estrutura gerenciada pacote usa a reflexão para obter o recurso correto de DLL, portanto, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> não definir esse argumento.|  
|NoShowAllView|REG\_DWORD|0 ou 1|Opcional.<br /><br /> Indica se um determinado  **Ferramentas Opções** página deve aparecer no modo complexo \(padrão\) de  **Ferramentas Opções** páginas.  Suporta ambientes de programação, como Visual Basic, que têm especial  **Ferramentas Opções** páginas agregadas configurações comuns para fornecer aos usuários especializadas Exibições simplificadas de opções.<br /><br /> Se a entrada REG\_DWORD é diferente de zero, o  **Ferramentas Opções** página não será exibida em uma exibição complexa.<br /><br /> Para mais informações, consulte [Caixa de diálogo Opções](../ide/reference/options-dialog-box-visual-studio.md).<br /><br /> Implementações baseadas na estrutura de pacote gerenciado podem definir esse valor, definindo a <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> propriedade `true` na <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.|  
  
 Um objeto com base em um único assembly de interoperabilidade ou VSPackage pode implementar mais de um  **Ferramentas Opções** página.  Cada implementação requer uma nova entrada de HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages.  
  
 Como o pacote gerenciado framework instancia o objeto fornecendo um  **Ferramentas Opções** página, cada página deve ter seu próprio objeto de implementação, independente da implementação do VSPackage da <xref:Microsoft.VisualStudio.Shell.Package>.  
  
## Suporte de automação  
 Se o suporte de automação é usado para implementar uma  **Ferramentas Opções** página, ele deve ser registrado como um provedor de automação.  Usar a automação para o gerenciamento de propriedade e usar seus mecanismos de persistência para salvar o  **Ferramentas Opções** página de estado, ele deve ser registrado como um `AutomationProperty` provedor.  
  
### Registrar um VSPackage como um provedor de automação \(apenas para páginas de opções de ferramentas baseadas em Assemblies de interoperabilidade\)  
 **Ferramentas Opções** páginas baseadas em um assembly de interoperabilidade são implementadas como parte de classes de implementação do VSPackage.  
  
 Nesse caso, se um  **Ferramentas Opções** página é oferecer suporte a automação, a interoperabilidade assembly–based VSPackage deve ser registrado como um provedor de automação.  
  
> [!NOTE]
>  Suporte de automação da estrutura de pacote gerenciado é fornecido por um objeto independente da implementação o VSPackage.  Se o objeto oferece suporte a automação, isso é registrado por meio de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> propriedade do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.  
  
 A entrada de registro VSPackage como um provedor de automação é do formulário HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\Packages\\*\<PackageGUID\>*\\Automation, onde  *\<Version\>* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como 8.0\) e  *\<PackageGUID\>* é o GUID do VSPackage implementa o objeto de automação.  
  
> [!NOTE]
>  O caminho raiz de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>* pode ser substituída por uma raiz alternativa quando o shell Visual Studio é inicializado.  Para mais informações, consulte [Opções de linha de comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 A estrutura da entrada do registro é:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\Packages\\*\<PackageGUID\>*\\Automation  
  
 `<AutomationObjectName>`  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|-----------|---------------|  
|Automação|REG\_SZ|Não definido|Indefinido.<br /><br /> A presença dessa chave indica que o VSPackage mencionado por  *\<PackageGUID\>* oferece suporte à automação.<br /><br /> O campo pode ser usado para armazenar a documentação.<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>cria automaticamente essa chave para aplicativos com base na estrutura de pacote gerenciado.|  
|`<AutomationObjectName>`|REG\_SZ|O nome canônico do objeto de automação fornecido|Somente o nome da chave é relevante.  Ele é usado em operações de automação.<br /><br /> O campo pode ser usado para armazenar a documentação.<br /><br /> Implementações baseadas na estrutura de pacote gerenciado, o nome desta chave é determinado da `name` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> construtor.<br /><br /> Se o <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> uma string válida fornecida para o construtor tem seu <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A> propriedade, esse valor é inserida aqui.|  
  
### Registrar uma página de opções de ferramentas, como suporte a automação  
 Implementações de assembly–based Framework– de pacote gerenciado e interoperabilidade de  **Ferramentas Opções** páginas devem registrar para permitir acesso de automação a um  **Ferramentas Opções** página.  Isso inclui mecanismos de persistência de propriedade de automação e acessar a página por meio de <xref:EnvDTE>.  Isso independe do registro VSPackage como um provedor de serviços de automação.  
  
 Como com a  **Ferramentas Opções** registro de página mencionado acima, a entrada tem uma chave primária com a categoria \(`<PageCategory>`\) do  **Ferramentas Opções** página e uma subchave que contém o nome da Subcategoria da página \(`<PageSubcategory>`\).  
  
 Se você usar a estrutura de pacote gerenciado, use <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para registrar uma classe como fornecendo uma  **Ferramentas Opções** página e definir o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> propriedade `true` para indicar que a página oferece suporte a automação.  
  
 A entrada do registro é encontrada em HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties, onde  *\<Version\>* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo 8.0.  
  
> [!NOTE]
>  O caminho raiz de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>* pode ser substituída por uma raiz alternativa quando o shell Visual Studio é inicializado, para obter mais informações, consulte [Opções de linha de comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 A estrutura da entrada do registro está abaixo:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\> \\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 Pacote \= '{YYYYYY aaaa aaaa aaaa YYYYYYYYY}'  
  
 Name \= '`<PageCategory>` .`<PageSubcategory>`'  
  
 'ProfileSave' \= 1\/0  
  
 A tabela a seguir lista os valores de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties\\`<PageCategory>`.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|-----------|---------------|  
|\(Padrão\)|REG\_SZ|O nome canônico de categoria de personalizado  **Ferramentas Opções** página|O nome da chave, `<PageCategory`\>, é o nome canônico não localizada do  **Ferramentas Opções** categoria de página. **Note:**  Se houver suporte para automação, os nomes canônicos de categoria e subcategoria não traduzidos são usados para obter um  **Ferramentas Opções** da página <xref:EnvDTE.Properties> coleção.  Para mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md). <br /><br /> A chave pode estar vazia ou pode conter a identificação de referência para a seqüência localizada na DLL de satélite da implementação.<br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, `<PageCategory`\> é obtida a partir de `categoryName` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Uma DLL de satélite contendo localizadas strings se VSPackage implementação não fornecê\-las.<br /><br /> Estrutura gerenciada pacote usa a reflexão para obter o recurso correto VSPackage, portanto, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> não definir esse argumento.|  
  
 A tabela a seguir lista os valores de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties\\`<PageCategory>\<PageSubCategory>`.  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|-----------|---------------|  
|\(Padrão\)|REG\_SZ|O nome da subcategoria do custom  **Ferramentas Opções** página|O nome da chave, `<PageSubCategory`\>, é o nome canônico não localizada do  **Ferramentas Opções** subcategoria de página. **Note:**  Se houver suporte para automação, os nomes canônicos de categoria e subcategoria não traduzidos são usados para obter um  **Ferramentas Opções** da página <xref:EnvDTE.Properties> coleção.  Para mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md). <br /><br /> A chave pode estar vazia ou pode conter a identificação de referência para a seqüência localizada na DLL de satélite da implementação.<br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, `<PageSubCategory>` é obtido do `pageName` argumento para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor.|  
|Pacote|REG\_SZ|GUID|O GUID do VSPackage implementando personalizado  **Ferramentas Opções** página.<br /><br /> Implementações baseiam a estrutura de pacote gerenciado usando <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usar a reflexão para obter esse valor.|  
|Nome|REG\_SZ|Nome da  **Ferramentas Opções** coleção de propriedades de página|O `<PageCategory>.<PageSubCategory>` seqüência de caracteres usada para se referir a  **Ferramentas Opções** página.  Para mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md).<br /><br /> Para implementações baseadas na estrutura de pacote gerenciado, o nome é obtido dos argumentos para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor e é do formulário `categoryName.pageName`.|  
|ProfileSave|DWORD|1\/0|Opcional.<br /><br /> Esse valor indica se o  **Ferramentas Opções** configurações de página são salvas pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações quando um usuário clica o  **Configurações de importação e exportação** comando o  **Ferramentas** menu.<br /><br /> Se a chave estiver presente e seu valor é 1, o  **Ferramentas Opções** página está solicitando suporte a configurações.<br /><br /> Implementações baseadas na estrutura de pacote gerenciado defina esse valor se o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> construtor é fornecido com o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propriedade definida `true`.|  
  
## Consulte também  
 [Criando scripts de escrivão](/visual-cpp/atl/creating-registrar-scripts)   
 [Usando páginas de opções](../misc/using-options-pages.md)   
 [Criando páginas de opções usando Assemblies de interoperabilidade](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [How to: Create Custom Options Pages](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Páginas de opções](../misc/options-pages.md)   
 [Suporte de automação para páginas de opções](../extensibility/internals/automation-support-for-options-pages.md)