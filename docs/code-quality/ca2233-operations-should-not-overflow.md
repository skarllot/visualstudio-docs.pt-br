---
title: "CA2233: as opera&#231;&#245;es n&#227;o devem estourar | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2233: as opera&#231;&#245;es n&#227;o devem estourar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método realiza uma operação aritmética e não valida os operandos com antecedência para evitar estouro.  
  
## Descrição da Regra  
 Operações aritméticas não devem ser executadas sem primeiro validar os operandos para garantir que o resultado da operação não está fora do intervalo de valores possíveis para os tipos de dados envolvidos.  Dependendo do contexto de execução e os tipos de dados envolvidos, o estouro aritmético pode resultar em <xref:System.OverflowException?displayProperty=fullName> ou a bit mais significativo de resultado descartado.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, valide os operandos antes de executar a operação.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se os valores possíveis dos operandos nunca causam a operação aritmética estouro.  
  
## Exemplo de uma Violação  
  
### Descrição  
 Um método no exemplo manipula um inteiro que viola esta regra.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requer a opção de estouro de inteiro de **Remover** ser desabilitado para que esse seja acionado.  
  
### Código  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Comentários  
 Se o método neste exemplo é <xref:System.Int32.MinValue?displayProperty=fullName>passado, a operação estouro negativo.  Isso faz com que o bit mais significativo de resultado a ser descartado.  As seguintes do código mostra como isso ocorre.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Saída  
  
```  
2147483647  
```  
  
## Correção com validação de parâmetro de entrada  
  
### Descrição  
 O exemplo a seguir corrige a violação anterior validando o valor de entrada.  
  
### Código  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## Correção com um bloco verificado  
  
### Descrição  
 O exemplo a seguir corrige a violação anterior envolvendo a operação em um bloco verificado.  Se a operação faz com que um estouro, <xref:System.OverflowException?displayProperty=fullName> será gerado.  
  
 Observe que os blocos verificados não tenham suporte em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### Código  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## Ativar o estouro aritmético\/estouro negativo verificados  
 Se você ativar o estouro aritmético\/estouro negativo verificados no C\#, é equivalente a envolver cada operação de inteiro em um bloco verificado.  
  
 **Para ativar verificado que o estouro aritmético\/estouro negativo em C\#**  
  
1.  Em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e escolha **Propriedades**.  
  
2.  Selecione a guia de **Compilar** e clique em **Avançado**.  
  
3.  **Verificar o estouro aritmético\/estouro negativo** Selecione e clique em **OK**.  
  
## Consulte também  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Operadores em C\#](/dotnet/csharp/language-reference/operators/index)   
 [Contexto verificado e não verificado](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)