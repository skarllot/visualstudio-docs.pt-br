---
title: "Criando p&#225;ginas de op&#231;&#245;es usando a automa&#231;&#227;o | Microsoft Docs"
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
  - "Páginas de opções de ferramentas [Visual Studio SDK], criando"
  - "automação [Visual Studio SDK], criando páginas de opções de ferramentas"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Criando p&#225;ginas de op&#231;&#245;es usando a automa&#231;&#227;o
Os VSPackages gerenciados pode usar a automação para estender o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado \(IDE\), adicionando  **Opções** páginas devem ser a  **Ferramentas** menu.  
  
 A  **Opções de ferramentas** página é fundamentalmente um controle de usuário e é codificada em da mesma maneira que qualquer outro controle de usuário.  Normalmente, você poderia utilizar um da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] designers do IDE para criar o objeto e adicionar controles de usuário.  
  
> [!NOTE]
>  **Ferram opções** páginas implementadas como uma caixa de diálogo caixa, usando um `DialogProc` para controlar mensagens do windows, deve ser caixas de diálogo sem janela restrita e não deve chamar o `EndDialog` função.  
  
 Você deve usar o objeto de automação que o VSPackage fornece o ambiente para oferecer suporte a propriedades de controle de usuário.  
  
## Suporte de automação para páginas de opções de ferramentas implementada com Assemblies de interoperabilidade  
 Para suportar o modelo de automação, VSPackage deve criar e registrar um objeto de automação.  Consulte [Oferecendo automação para VSPackages](../extensibility/internals/providing-automation-for-vspackages.md) para obter mais informações.  
  
 Quando o código que usa o modelo de automação chama `DTE.Properties` para a coleção de propriedades de um determinado  **Opções de ferramentas** página, o IDE usa o objeto de automação fornecido pela implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> para retornar a coleção e permitir o acesso ao seu constituinte <xref:EnvDTE.Property> objetos.  
  
 **Nota** o objeto de automação retornado por <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> varia de acordo com o GUID fornecido \(como um VSPackage pode oferecer suporte a mais de um objeto de automação\).  Para obter mais informações sobre como implementar objetos de automação, consulte [Suporte de automação para páginas de opções](../extensibility/internals/automation-support-for-options-pages.md).  
  
 A  **Opções de ferramentas** página é especificada por dois identificadores.  O identificador a primeiro é uma seqüência de caracteres que indica a pasta que contém o item no  **Opções** seção a  **Ferramentas** menu.  O segundo identificador é uma seqüência de caracteres que indica o item específico na pasta.  Para obter mais informações, consulte [Usando páginas de opções](../misc/using-options-pages.md).  
  
 Duas entradas de registro são necessários para registrar um objeto de automação:  
  
-   Em HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versão* \\Packages\\*\<PackageGUID\>*\\Automation  
  
-   Em HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties  
  
     onde  *\<Version\>* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como 8.0\) e  *\<PackageGUID\>* é o GUID do VSPackage que implementa o objeto de automação.  
  
 Dependendo da configuração da entrada do registro de AutomationProperties, o estado de um  **Opções de ferramentas** página pode ser automaticamente salva e restaurada por meio a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações quando um usuário seleciona a  **Configurações de importação\/exportação** no  **Ferramentas** menu.  Para obter mais informações sobre como salvar  **Opções de ferramentas** página de configurações, consulte [Registrando páginas de opções personalizadas](../misc/registering-custom-options-pages.md).  
  
 Um aplicativo não pode usar o modelo de automação para implementar suporte em um  **Opções de ferramentas** da página Propriedades e configurações.  
  
 Isso pode ser desejável por vários motivos:  
  
-   As configurações são manipuladas pelo  **Opções de ferramentas** página são mais complexas na estrutura do que o que suporta o modelo de propriedade de automação relativamente plana.  
  
-   É necessário para impedir que outros aplicativos programaticamente gerenciando sua  **Opções de ferramentas** página.  
  
-   Controles de acesso especial ou de recursos de segurança são necessários.  
  
 Nesses casos, pode implementar os VSPackages  **Opções de ferramentas** página de suporte em qualquer forma que seja apropriado.  No entanto, eles precisam:  
  
-   Lidar com a configuração de  **Opções de ferramentas** propriedades da página.  
  
-   Gerenciar a persistência de  **Ferramentas Opções** estado por meio da página da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] configurações.  
  
-   Fornecer uma API, se desejado, para outros aplicativos usar o  **Opções de ferramentas** página.  
  
 As propriedades da  **fontes e cores** caixa de diálogo é um exemplo de um  **Opções de ferramentas** página não pode ser modificada por meio do modelo de automação.  Em vez disso, uma API separada for fornecida, com base na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface para permitir que a manipulação programática da  **fontes e coresOpções de ferramentas** página.  Para obter mais informações sobre como controlar a  **fontes e coresOpções de ferramentas** de página, consulte [Usando fontes e cores](../extensibility/using-fonts-and-colors.md).  
  
## Suporte de automação para páginas de opções de ferramentas dentro da estrutura de pacote gerenciado  
 Definir o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> do registro de propriedade de uma implementação <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> instância para indicar que uma implementação de Framework\-base do pacote de gerenciamento de um  **Opções de ferramentas** página oferece suporte à automação.  
  
 **Ferram opções** páginas derivada de <xref:Microsoft.VisualStudio.Shell.DialogPage> são fornecidos com um objeto de automação padrão, que pode ser substituído.  
  
 Se um  **Ferramentas Opções** a implementação de página não oferece suporte a automação, a implementação deve fornecer sua própria API para permitir o acesso programático para o  **Ferramentas Opções** página.  
  
> [!NOTE]
>  O IDE  **fontes e cores** página é um exemplo de um  **Opções de ferramentas** página que não oferece suporte a automação, mas fornece acesso ao  **Ferramentas Opções** página por meio de sua própria API.  Para obter mais informações, consulte [Usando fontes e cores](../extensibility/using-fonts-and-colors.md).  
  
## Consulte também  
 [Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Criando páginas de opções usando Assemblies de interoperabilidade](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Criando páginas de opções](../extensibility/internals/creating-options-pages.md)   
 [How to: Create Custom Options Pages](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Criando scripts de escrivão](/visual-cpp/atl/creating-registrar-scripts)   
 [Suporte de automação para páginas de opções](../extensibility/internals/automation-support-for-options-pages.md)   
 [Usando páginas de opções](../misc/using-options-pages.md)