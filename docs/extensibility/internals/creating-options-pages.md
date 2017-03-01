---
title: "Criando páginas de opções | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
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
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>Criando páginas de opções
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estrutura de pacote gerenciado, as classes derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage>estender o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE adicionando **opções** páginas sob o **ferramentas** menu.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Um objeto que implementa um determinado **opção ferramentas** página estiver associada a VSPackages específicos, o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>objeto.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Como o ambiente instancia o objeto que implementa uma determinada **opções de ferramentas** página quando a página específica é exibida pelo IDE:  
  
-   A **opção ferramentas** página deve ser implementada em seu próprio objeto e não no objeto implementando um VSPackage.  
  
-   Um objeto não pode implementar vários **opções de ferramentas** páginas.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrar como um provedor de página de opções de ferramentas  
 Uma configuração de usuário de suporte de VSPackage por meio de **opções de ferramentas** páginas indica os objetos fornecendo **opções de ferramentas** páginas aplicando instâncias de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>aplicada para o <xref:Microsoft.VisualStudio.Shell.Package>implementação.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Deve haver uma instância de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>para cada <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivado do tipo que implementa um **opções de ferramentas** página.</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Cada instância de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>usa o tipo que implementa o **opções de ferramentas** página cadeias de caracteres que contêm a categoria e subcategoria usado para identificar um **opções de ferramentas** página e informações sobre o recurso para registrar o tipo como fornecendo uma **opções de ferramentas** página.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>Persistir estado da página Opções de ferramentas  
 Se um **opções de ferramentas** implementação de página está registrada com o suporte de automação habilitado, o IDE persiste o estado da página juntamente com todos os outros **opções de ferramentas** páginas.  
  
 Um VSPackage pode gerenciar sua própria persistência usando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Apenas um ou outro método de persistência deve ser usado.  
  
## <a name="implementing-dialogpage-class"></a>A implementação da classe DialogPage  
 Um objeto que fornece a implementação do VSPackage um <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivado pode tirar proveito dos seguintes recursos herdados:</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   Uma janela de interface de usuário padrão.  
  
-   Um padrão disponível do mecanismo de persistência ambos se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>é aplicado à classe, ou se o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>está definida como `true` para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>que é aplicado à classe.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   Suporte de automação.  
  
 O requisito mínimo para um objeto que implementa um **opções de ferramentas** página usando <xref:Microsoft.VisualStudio.Shell.DialogPage>é a adição de propriedades públicas.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Se a classe corretamente registrado como um **opções de ferramentas** página suas propriedades públicas estão disponíveis no provedor, o **opções** seção o **ferramentas** menu na forma de uma grade de propriedade.  
  
 Todos esses recursos padrão podem ser substituídos. Por exemplo, para criar uma mais sofisticada interface de usuário requer somente substituir a implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>  
  
## <a name="example"></a>Exemplo  
 O que vem a seguir é uma implementação simples "hello world" de uma página de opções. Adicionando o seguinte código a um projeto padrão criado pelo modelo de pacote Visual Studio com o **o comando de Menu** opção selecionada adequadamente demonstrará a funcionalidade da página de opção.  
  
### <a name="description"></a>Descrição  
 A classe a seguir define uma página de opções mínimo "hello world". Quando aberto, o usuário pode definir o público `HelloWorld` propriedade em uma grade de propriedade.  
  
### <a name="code"></a>Código  
 [!code-cs[N º&11; UI_UserSettings_ToolsOptionPages](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages n º&11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descrição  
 Aplicar o atributo a seguir à classe de pacote disponibiliza as opções de página quando o pacote for carregado. Os números são arbitrários IDs de recurso para a categoria e a página, e o valor booliano no final Especifica se a página oferece suporte à automação.  
  
### <a name="code"></a>Código  
 [!code-cs[UI_UserSettings_ToolsOptionPages &#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descrição  
 O manipulador de eventos a seguir exibe um resultado dependendo do valor da propriedade definida na página de opções. Ele usa o <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>método com o resultado explicitamente convertido no tipo de página de opção personalizada para acessar as propriedades expostas pela página.</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 No caso de um projeto gerado pelo modelo de pacote, chame essa função do `MenuItemCallback` função anexá-lo para o comando padrão é adicionado para o **ferramentas** menu.  
  
### <a name="code"></a>Código  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Opções e configurações de usuário estendendo](../../extensibility/extending-user-settings-and-options.md)   
 [Suporte de automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)
