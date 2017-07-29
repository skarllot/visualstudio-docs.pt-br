---
title: Como dividir uma classe em classes parciais (Designer de Classe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9d74565f8e7e5b89e1716e9e2d88e2e18e077124
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Como dividir uma classe em classes parciais (Designer de Classe)
Você pode dividir a declaração de uma classe ou estrutura entre várias declarações usando a palavra-chave `Partial` no Visual Basic ou a palavra-chave `partial` no Visual C#. É possível usar quantas declarações parciais você desejar, em quantos arquivos de origem diferentes desejar ou em um único arquivo de origem. No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.  
  
 Classes parciais são úteis em várias situações. Por exemplo, quando você estiver trabalhando em projetos grandes, separar uma classe em mais de um arquivo permite que mais de um programador trabalhe ao mesmo tempo. Quando estiver trabalhando com código gerado pelo Visual Studio, você pode alterar a classe sem precisar recriar o arquivo de origem. (Exemplos de códigos gerados pelo Visual Studio incluem código de wrapper do serviço Web e do Windows Forms). Portanto, você pode criar um código que usa classes geradas automaticamente sem precisar modificar o arquivo que o Visual Studio cria.  
  
 Existem dois tipos de métodos parciais. No Visual C#, eles são chamados de declarar e implementar. No Visual Basic, são chamados de declaração e implementação.  
  
 O Designer de Classe dá suporte a métodos e classes parciais. A forma de tipo no diagrama de classe se refere a um único local de declaração para a classe parcial. Se a classe parcial for definida em vários arquivos, você pode especificar qual local de declaração o Designer de Classe usará definindo a propriedade **Localização de Novo Membro** na janela **Propriedades**. Ou seja, quando você clica duas vezes em uma forma de classe, o Designer de Classe vai até o arquivo de origem que contém a declaração de classe identificada pela propriedade **Localização de Novo Membro**. Quando você clica duas vezes em um método parcial em uma forma de classe, o Designer de Classe vai para a declaração de método parcial. Além disso, na janela **Propriedades**, a propriedade **Nome de Arquivo** aponta para o local da declaração. Para classes parciais, **Nome de Arquivo** lista todos os arquivos que contêm código de implementação e declaração dessa classe. No entanto, para métodos parciais, **Nome de Arquivo** lista apenas o arquivo que contém a declaração de método parcial.  
  
 Os exemplos a seguir dividem a definição da classe `Employee` em duas declarações, cada uma das quais define um procedimento diferente. As duas definições parciais nos exemplos podem estar em um arquivo de origem ou em dois arquivos de origem diferentes.  
  
> [!NOTE]
>  O Visual Basic usa definições de classe parcial para separar o código gerado pelo Visual Studio do código de autoria do usuário. O código é separado em arquivos de origem distintos. Por exemplo, o **Windows Form Designer** define classes parciais para controles, como `Form`. Você não deve modificar o código gerado nesses controles.  
  
 Para obter mais informações sobre tipos parciais no Visual Basic, consulte [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Exemplo  
 Para dividir uma definição de classe no Visual Basic, use a palavra-chave `Partial`, conforme mostrado no exemplo a seguir.  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## <a name="example"></a>Exemplo  
 Para dividir uma definição de classe no Visual C#, use a palavra-chave `partial`, conforme mostrado no exemplo a seguir.  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Classes e métodos parciais](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [parcial (tipo)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [parcial (método) (Referência de C#)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)
