---
title: Escolher itens da caixa de ferramentas, componentes do WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8d34a09ec4716a9ab2d5fbaea6c93657961c1c43
ms.lasthandoff: 02/22/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>Escolher Itens da Caixa de Ferramentas, Componentes WPF
Essa guia da caixa de diálogo **Escolher Itens da Caixa de Ferramentas** exibe uma lista de controles do WPF (Windows Presentation Foundation) disponíveis no computador local. Para exibir essa lista, selecione **Escolher Itens da Caixa de Ferramentas** no menu **Ferramentas** para exibir a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** e, em seguida, selecione a guia **Componentes do WPF**. Para classificar os componentes listados, selecione todo o título de coluna.  
  
-   Quando a caixa de seleção ao lado de um componente for selecionada, um ícone desse componente será exibido na **Caixa de ferramentas**.  
  
    > [!TIP]
    >  Para adicionar uma instância de um controle WPF a um documento de projeto aberto para edição, arraste seu ícone **Caixa de ferramentas** para a superfície do modo de exibição de Design. Uma marcação e um código padrão do componente são inseridos no projeto, prontos para modificação. Para obter mais informações, consulte [Como gerenciar a janela de ferramentas](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) e [Como manipular as guias da caixa de ferramentas](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
-   Quando a caixa de seleção ao lado de um componente for desmarcada, o ícone correspondente será removido da **Caixa de ferramentas.**  
  
    > [!NOTE]
    >  Os componentes do .NET Framework instalados no computador permanecem disponíveis independentemente de seus ícones serem exibidos ou não na **Caixa de ferramentas**.  
  
 As colunas da guia **Componentes do WPF** contêm as seguintes informações:  
  
 Nome  
 Lista os nomes dos controles WPF para os quais existem entradas no Registro do computador.  
  
 espaço de nome  
 Exibe a hierarquia do namespace [NIB: Biblioteca de classes .NET Framework](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) que define a estrutura do componente. Classifique essa coluna para listar os componentes disponíveis em cada namespace do .NET Framework instalado no computador.  
  
 Nome do Assembly  
 Exibe o nome do assembly do .NET Framework que inclui o namespace de cada componente. Classifique essa coluna para listar os namespaces contidos em cada assembly do .NET Framework instalado no computador.  
  
 Diretório  
 Exibe o local do assembly do .NET Framework. O local padrão para todos os assemblies é o cachê global de assemblies. Para obter mais informações sobre o Cache de Assembly Global, consulte [Trabalhando com assemblies e o cache de assembly global](http://msdn.microsoft.com/Library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
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
 A adição de um controle personalizado ou de <xref:System.Windows.Controls.UserControl> à Caixa de ferramentas tem as limitações a seguir.  
  
-   Funciona somente para controles personalizados definidos fora do projeto atual.  
  
-   Não atualize corretamente ao alterar a configuração de solução de Depuração para Versão ou de Versão para Depuração. Isso ocorre porque a referência não é uma referência de projeto, mas refere-se ao assembly no disco. Se o controle fizer parte da solução atual, ao alterar de Depuração para Versão, o projeto continuará referenciando a versão de Depuração do controle.  
  
 Além disso, se os metadados em tempo de design forem aplicados ao controle personalizado e esses metadados especificarem que o <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> é definido como `false`, o controle não será exibido na Caixa de ferramentas.  
  
 É possível referenciar os controles diretamente no modo de exibição XAML, mapeando o namespace e o assembly do controle. Para obter mais informações, consulte [Como importar um namespace no XAML](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Caixa de ferramentas](../../ide/reference/toolbox.md)   
 [Como usar um controle WPF de terceiros em um aplicativo WPF](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [Designer do WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
