---
title: Escolher itens da caixa de ferramentas, componentes do WPF | Microsoft Docs
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: b574aef447309842b5ff02be72dae291407f0ddb
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>Escolher Itens da Caixa de Ferramentas, Componentes WPF
Essa guia da caixa de diálogo **Escolher Itens da Caixa de Ferramentas** exibe uma lista de controles do WPF (Windows Presentation Foundation) disponíveis no computador local. Para exibir essa lista, selecione **Escolher Itens da Caixa de Ferramentas** no menu **Ferramentas** para exibir a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** e, em seguida, selecione a guia **Componentes do WPF**. Para classificar os componentes listados, selecione todo o título de coluna.  

-   Quando a caixa de seleção ao lado de um componente for selecionada, um ícone desse componente será exibido na **Caixa de ferramentas**.  

    > [!TIP]
    >  Para adicionar uma instância de um controle WPF a um documento de projeto aberto para edição, arraste seu ícone **Caixa de ferramentas** para a superfície do modo de exibição de Design. Uma marcação e um código padrão do componente são inseridos no projeto, prontos para modificação. Para obter mais informações, consulte [Usando a caixa de ferramentas](../../ide/using-the-toolbox.md).  

-   Quando a caixa de seleção ao lado de um componente for desmarcada, o ícone correspondente será removido da **Caixa de ferramentas.**  

    > [!NOTE]
    >  Os componentes do .NET Framework instalados no computador permanecem disponíveis independentemente de seus ícones serem exibidos ou não na **Caixa de ferramentas**.  

 As colunas da guia **Componentes do WPF** contêm as seguintes informações:  

 Nome  
 Lista os nomes dos controles WPF para os quais existem entradas no Registro do computador.  

 Namespace  
 Exibe a hierarquia do namespace [API de classes do .NET Framework](/dotnet/api/?view=netframework-4.7) que define a estrutura do componente. Classifique essa coluna para listar os componentes disponíveis em cada namespace do .NET Framework instalado no computador.  

 Nome do Assembly  
 Exibe o nome do assembly do .NET Framework que inclui o namespace de cada componente. Classifique essa coluna para listar os namespaces contidos em cada assembly do .NET Framework instalado no computador.  

 Diretório  
 Exibe o local do assembly do .NET Framework. O local padrão para todos os assemblies é o cachê global de assemblies. Para obter mais informações sobre o Cache de Assembly Global, consulte [Trabalhando com assemblies e o cache de assembly global](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).  

## <a name="uielement-list"></a>Lista UIElement  
 **Filtrar**  
 Filtra a lista de controles WPF com base na cadeia de caracteres fornecida na caixa de texto. Todas as correspondências de uma das quatro colunas são mostradas.  

 **Limpar**  
 Limpa a cadeia de caracteres de filtro.  

 **Procurar**  
 Abre a caixa de diálogo **Abrir**, que permite navegar para assemblies que contêm controles WPF. Use isso para carregar assemblies que não estão localizados no Cache de Assembly Global.  

 **Linguagem**  
 Mostra o idioma localizado do assembly que contém o controle WPF selecionado.  

## <a name="limitations"></a>Limitações  
 A adição de um controle personalizado ou um <xref:System.Windows.Controls.UserControl> à caixa de ferramentas apresenta as seguintes limitações.  

-   Funciona somente para controles personalizados definidos fora do projeto atual.  

-   Não atualize corretamente ao alterar a configuração de solução de Depuração para Versão ou de Versão para Depuração. Isso ocorre porque a referência não é uma referência de projeto, mas refere-se ao assembly no disco. Se o controle fizer parte da solução atual, ao alterar de Depuração para Versão, o projeto continuará referenciando a versão de Depuração do controle.  

 Além disso, se os metadados em tempo de design forem aplicados ao controle personalizado e esses metadados especificarem que o <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> é definido como `false`, o controle não será exibido na Caixa de Ferramentas.  

 É possível referenciar os controles diretamente no modo de exibição XAML, mapeando o namespace e o assembly do controle.  

## <a name="see-also"></a>Consulte também  
 [Caixa de Ferramentas](../../ide/reference/toolbox.md)

 [Introdução ao WPF](../../designers/getting-started-with-wpf.md)

