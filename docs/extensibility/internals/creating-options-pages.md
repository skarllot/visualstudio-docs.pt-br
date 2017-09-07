---
title: "Criando páginas de opções | Microsoft Docs"
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6ed61dbc745b00f5f6f0beeba5aa38c3d316f98f
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="creating-options-pages"></a>Criando páginas de opções
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estrutura de pacote gerenciado, as classes derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> estender o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE adicionando **opções** páginas no **ferramentas** menu.  
  
 Um objeto que implementa um determinado **opção ferramentas** página estiver associada a VSPackages específicos, o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.  
  
 Porque o ambiente instancia o objeto que implementa um determinado **Ferramentas opções** página quando a página específica é exibida pelo IDE:  
  
-   Um **opção ferramentas** página deve ser implementada em seu próprio objeto e não no objeto que implementa um VSPackage.  
  
-   Um objeto não pode implementar vários **Ferramentas opções** páginas.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrar como um provedor de página de opções de ferramentas  
 Uma configuração de usuário de suporte de VSPackage por meio de **Ferramentas opções** páginas indica os objetos fornecendo **Ferramentas opções** páginas aplicando instâncias do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicada para o <xref:Microsoft.VisualStudio.Shell.Package>implementação.  
  
 Deve haver uma instância de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivado do tipo que implementa um **Ferramentas opções** página.  
  
 Cada instância do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usa o tipo que implementa o **Ferramentas opções** página cadeias de caracteres que contêm a categoria e subcategoria, usado para identificar um **Ferramentas opções** página e recursos informações para registrar o tipo como fornecendo uma **Ferramentas opções** página.  
  
## <a name="persisting-tools-options-page-state"></a>Persistir estado da página Opções de ferramentas  
 Se um **Ferramentas opções** implementação da página está registrada com o suporte de automação de habilitado, o IDE persiste o estado da página junto com todos os outros **Ferramentas opções** páginas.  
  
 Um VSPackage pode gerenciar seu próprio persistência usando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Deve ser usado apenas um ou outro método de persistência.  
  
## <a name="implementing-dialogpage-class"></a>A implementação da classe de DialogPage  
 Um objeto que fornece a implementação do VSPackage um <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivado pode tirar proveito dos recursos herdados a seguir:  
  
-   Uma janela de interface de usuário padrão.  
  
-   Um padrão de mecanismo de persistência disponível ou se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> é aplicado à classe, ou se o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> está definida como `true` para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que é aplicado à classe.  
  
-   Suporte de automação.  
  
 O requisito mínimo para um objeto que implementa um **Ferramentas opções** página usando <xref:Microsoft.VisualStudio.Shell.DialogPage> é a adição de propriedades públicas.  
  
 Se a classe corretamente registrado como um **Ferramentas opções** página provedor, e suas propriedades públicas estão disponíveis no **opções** seção o **ferramentas** menu na forma de um grade de propriedade.  
  
 Todos esses recursos padrão podem ser substituídos. Por exemplo, para criar um usuário mais sofisticado interface requer apenas substituir a implementação padrão de <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Exemplo  
 O que vem a seguir é uma implementação simples "hello world" de uma página de opções. Adicionando o seguinte código a um projeto padrão criado pelo modelo do pacote Visual Studio com o **comando de Menu** opção selecionada adequadamente demonstrar a funcionalidade de página de opção.  
  
### <a name="description"></a>Descrição  
 A classe a seguir define uma página de opções "hello world" mínimo. Quando aberto, o usuário pode definir o público `HelloWorld` propriedade em uma grade de propriedade.  
  
### <a name="code"></a>Código  
 [!code-csharp[N º 11 do UI_UserSettings_ToolsOptionPages](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages n º 11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descrição  
 Aplicar o seguinte atributo para a classe de pacote disponibiliza as opções de página quando o pacote for carregado. Os números são arbitrários IDs de recurso para a categoria e a página e o valor booliano no final Especifica se a página dá suporte à automação.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descrição  
 O manipulador de eventos a seguir exibe um resultado, dependendo do valor da propriedade definida na página de opções. Ele usa o <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método com o resultado convertido explicitamente no tipo de página de opção personalizada para acessar as propriedades expostas pela página.  
  
 No caso de um projeto gerado pelo modelo de pacote, chame essa função do `MenuItemCallback` função para anexá-lo para o comando padrão é adicionada para o **ferramentas** menu.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Opções e configurações de usuário de extensão](../../extensibility/extending-user-settings-and-options.md)   
 [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)
