---
title: "Suporte para a barra de navegação em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Suporte para a barra de navegação em um serviço de linguagem herdado
Barra de navegação na parte superior do editor de modo de exibição exibe os tipos e membros no arquivo. Tipos são mostrados no menu suspenso à esquerda e membros são mostrados na parte direita lista suspensa. Quando o usuário seleciona um tipo, o cursor é colocado na primeira linha do tipo. Quando o usuário seleciona um membro, o cursor é colocado na definição do membro. As caixas suspensas são atualizadas para refletir o local atual do cursor.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Exibir e atualizar a barra de navegação  
 Para oferecer suporte a barra de navegação, você deve derivar uma classe a partir de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe e implementar a <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Quando o serviço de linguagem recebe uma janela de código, a base de <xref:Microsoft.VisualStudio.Package.LanguageService>classe instancia o <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, que contém o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>objeto que representa a janela de código.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> O <xref:Microsoft.VisualStudio.Package.CodeWindowManager>objeto recebe um novo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> O <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>método obtém uma <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objeto.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Se você retornar uma instância do seu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe, o <xref:Microsoft.VisualStudio.Package.CodeWindowManager>chamadas seu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>para popular o interno lista e passa seu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>o objeto para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] suspensa barra manager.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Na lista suspensa barra manager, por sua vez, chama o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>método no seu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objeto para estabelecer o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>objeto que contém as duas barras de menu suspenso.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 Quando o cursor é movido, o <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>chamadas de método de <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>método.</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> A base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>método chama o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método em sua <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe para atualizar o estado da barra de navegação.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Você passa um conjunto de <xref:Microsoft.VisualStudio.Package.DropDownMember>objetos para esse método.</xref:Microsoft.VisualStudio.Package.DropDownMember> Cada objeto representa uma entrada na lista suspensa.  
  
## <a name="the-contents-of-the-navigation-bar"></a>O conteúdo da barra de navegação  
 Barra de navegação geralmente contém uma lista de tipos e uma lista de membros. A lista de tipos inclui todos os tipos disponíveis no arquivo de origem atual. Os nomes de tipo incluem as informações do namespace completo. Este é um exemplo de código em c# com dois tipos:  
  
```c#  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 A lista de tipo exibirá `TestLanguagePackage.TestLanguageService` e `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 A lista de membros exibe os membros do tipo selecionado na lista de tipos disponíveis. Usando o exemplo de código acima, se `TestLanguagePackage.TestLanguageService` é o tipo que é selecionado, a lista de membros conteria os membros privados `tokens` e `serviceName`. A estrutura interna `Token` não é exibido.  
  
 Você pode implementar a lista de membros para colocar o nome de um membro em negrito quando o cursor é colocado dentro dele. Membros também podem ser exibidos em esmaecida texto, indicando que eles não estão no escopo em que o cursor está posicionado no momento.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Habilitando o suporte à barra de navegação  
 Para habilitar o suporte para a barra de navegação, você deve definir o `ShowDropdownBarOption` parâmetro o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>atributo `true`.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Esse parâmetro define o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>propriedade.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Para oferecer suporte a barra de navegação, você deve implementar o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objeto no <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 Na implementação do <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>método, se o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>está definida como `true`, você pode retornar um <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>objeto.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Se você não retornam o objeto, a barra de navegação não será exibida.  
  
 A opção para mostrar a barra de navegação pode ser definida pelo usuário, portanto, é possível para esse controle devem ser redefinidos enquanto a exibição do editor é aberta. O usuário deve fechar e reabrir a janela do editor antes que a alteração entre em vigor.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementação de suporte para a barra de navegação  
 O <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método usa duas listas (uma para cada lista suspensa) e dois valores que representa a seleção atual em cada lista.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> As listas e os valores de seleção podem ser atualizados, caso em que o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método deve retornar `true` para indicar que as listas foram alteradas.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 Como a seleção é alterada em tipos de lista suspensa, a lista de membros deve ser atualizada para refletir o novo tipo. O que é mostrado na lista de membros pode ser:  
  
-   A lista de membros para o tipo atual.  
  
-   Todos os membros disponíveis na fonte de arquivo, mas com todos os membros não o tipo atual exibido em texto cinza. O usuário ainda pode selecionar os membros de cinza, para que eles podem ser usados para navegação rápida, mas a cor indica que não são parte do tipo selecionado.  
  
 Uma implementação de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método normalmente executa as seguintes etapas:</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  Obter uma lista de declarações atuais para o arquivo de origem.  
  
     Há várias formas para preencher a lista. Uma abordagem é criar um método personalizado em sua versão do <xref:Microsoft.VisualStudio.Package.LanguageService>classe chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método com um motivo para a análise personalizada que retorna uma lista de todas as declarações.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Outra abordagem seria chamar o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método diretamente do <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método com o motivo de análise personalizada.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Uma terceira abordagem seria armazenar em cache as declarações no <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe retornados pela última operação de análise completa no <xref:Microsoft.VisualStudio.Package.LanguageService>de classe e recuperá-lo do <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  Preencher ou atualizar a lista de tipos.  
  
     O conteúdo da lista de tipos poderá ser atualizado quando a origem tiver alterado ou se você optou por alterar o estilo do texto dos tipos com base na posição atual do cursor. Observe que essa posição é passada para o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>método.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  Determine o tipo para selecionar na lista de tipos com base na posição atual do cursor.  
  
     Você pode pesquisar as declarações que foram obtidas na etapa 1 para localizar o tipo que inclui a posição atual do cursor e procure na lista de tipos para esse tipo determinar seu índice na lista de tipos.  
  
4.  Preencher ou atualizar a lista de membros com base no tipo selecionado.  
  
     A lista de membros reflete o que é exibido no momento o **membros** lista suspensa. O conteúdo da lista de membros talvez precise ser atualizada se a origem tiver alterado ou se você estiver exibindo somente os membros do tipo selecionado e o tipo selecionado foi alterado. Se você optar por exibir todos os membros no arquivo de origem, o estilo do texto de cada membro da lista precisa ser atualizado se o tipo selecionado foi alterado.  
  
5.  Determine o membro para selecionar na lista de membros com base na posição atual do cursor.  
  
     Pesquise as declarações que foram obtidas na etapa 1 para o membro que contém a posição atual do cursor e pesquisar a lista de membros para esse membro determinar seu índice na lista de membros.  
  
6.  Retornar `true` se as alterações foram feitas para as listas ou as seleções na lista.
