---
title: 'Passo a passo: exemplo de LinqToXmlDataBinding | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ec8e44f5299154b0781a16c43ba485c1be076467
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Passo a passo: Exemplo de LinqToXmlDataBinding
Essa explicação passo a passo descreve o exemplo de LinqToXmlDataBinding, e explica algumas de conteúdo mais interessantes de seus dois arquivos de fonte primária, L2DBForm.xaml e L2DBForm.xaml.cs.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Antes de ler este passo-a-passo, é altamente recomendável compilar e executar o programa LinqToXmlDataBinding conforme descrito em [Como compilar e executar o exemplo de LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Comentários  
 O programa de LinqToXmlDataBinding é um aplicativo Windows Presentation Foundation (WPF) composto de arquivos de origem C# e XAML. Contém um documento XML inserido que define uma lista de livros, e permite que o usuário para exibir, adicionar, excluir, e editar essas entradas. É composto de dois seguintes arquivos de fonte primária:  
  
-   L2DBForm.xaml contém o código de declaração XAML para a interface do usuário (UI) da janela principal. Também contém uma seção de recursos da janela que define um provedor de dados e um documento XML inserido para as listagens de livro.  
  
-   L2DBForm.xaml.cs contém os métodos de inicialização e de manipulação de eventos associados com a interface do usuário.  
  
 A janela principal é dividida nas quatro seções verticais de interface de usuário:  
  
-   **XML** exibe o código-fonte XML bruto da listagem de livros inserida.  
  
-   **Lista de livros** exibe as entradas de livro como texto padrão e permite que o usuário selecione e exclua entradas individuais.  
  
-   **Editar Livro Selecionado** permite que o usuário edite os valores associados à entrada do livro selecionada no momento.  
  
-   **Adicionar Novo Livro** habilita a criação de uma nova entrada de livro com base nos valores inseridos pelo usuário.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Código-fonte de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Contém o conteúdo e a descrição de código XAML no arquivo L2DBForm.xaml.|  
|[Código-fonte de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Contém o conteúdo e a descrição do código-fonte C# no arquivo L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>Consulte também  
 [Vinculação de dados de WPF usando o exemplo LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Como compilar e executar o exemplo de LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
