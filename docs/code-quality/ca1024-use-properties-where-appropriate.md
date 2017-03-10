---
title: "CA1024: usar propriedades quando apropriado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1024: usar propriedades quando apropriado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um método protegido têm um nome que começa com `Get`, não usa nenhum parâmetro, e retornam um valor que não é uma matriz.  
  
## Descrição da Regra  
 Na maioria dos casos, as propriedades representam dados e os métodos executam ações.  As propriedades são acessadas como campos, que os torna mais fácil usar.  Um método é uma boa candidata a se tornar uma propriedade se uma destas condições estiver presente:  
  
-   Não usa nenhum argumento e retorna informações do estado de um objeto.  
  
-   Aceita um único argumento para definir qualquer parte do estado de um objeto.  
  
 As propriedades devem se comportar como se fossem campos; se o método não pode, não deve ser alterado para uma propriedade.  Os métodos são melhor do que propriedades nas seguintes situações:  
  
-   O método executa uma operação demorada.  O método é perceivably mais lento do que o tempo necessário para definir ou obter o valor de um campo.  
  
-   O método executa uma conversão.  Acessando um campo não retorna uma versão convertida de dados que armazenam.  
  
-   O método obter tem um efeito colateral observável.  Recuperando o valor de um campo não gerencia nenhum efeito colateral.  
  
-   A ordem de execução é importante.  Defina o valor de um campo não confie na ocorrência de outras operações.  
  
-   Chame o método duas vezes cria sucessivamente resultados diferentes.  
  
-   O método é estática mas retorna um objeto que pode ser modificado pelo chamador.  Recuperar o valor de um campo não permite que o chamador modificar os dados que são armazenados pelo campo.  
  
-   O método retorna uma matriz.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o método a uma propriedade.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se o método localiza pelo menos um dos critérios listados anteriormente.  
  
## Expansão de controle da propriedade no depurador  
 Os desenvolvedores de uma razão para usar uma propriedade é porque não desejam que o depurador automática para a expanda.  Por exemplo, a propriedade pode envolver atribuir um objeto grande ou chame um P\/Invoke, mas não pode realmente ter nenhum efeito colateral perceptíveis.  
  
 Você pode evitar o depurador propriedades automática expandindo aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>.  O exemplo a seguir mostra esse atributo que está sendo aplicado a uma propriedade da instância.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## Exemplo  
 O exemplo a seguir contém vários métodos que devem ser convertidos em propriedades, e vários que não devem porque não se comportam como campos.  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]