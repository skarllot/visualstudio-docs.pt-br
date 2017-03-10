---
title: "CA2000: descartar objetos antes de perder o escopo | Microsoft Docs"
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
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000: descartar objetos antes de perder o escopo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Categoria|Microsoft.Reliability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um objeto local de um tipo <xref:System.IDisposable> é criado mas o objeto não é descartado antes todas as referências para o objeto estarem fora do escopo.  
  
## Descrição da Regra  
 Se um objeto descartável não é descartado explicitamente antes de todas as referências a ele estarem fora do escopo, o objeto será descartado em algum tempo indefinido quando o coletor de lixo executa o finalizador do objeto.  Porque um evento excepcional pode ocorrer que impeça o finalizador do objeto de executar, o objeto deve ser explicitamente descartado para evitar isso.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame <xref:System.IDisposable.Dispose%2A> no objeto antes todas as referências a ele estarem fora do escopo.  
  
 Observe que você pode usar a instrução `using` \(`Using` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) para envolver os objetos que implementam `IDisposable`.  Os objetos que estão envolvidos assim, serão descartados automaticamente no fechamento do bloco `using`.  
  
 A seguir estão algumas situações onde a instrução using não é suficiente para proteger objetos IDisposable e pode fazer com que CA2000 ocorra.  
  
-   Retornar um objeto descartável requer que o objeto seja construído em um bloco try\/finally de fora de um bloco using.  
  
-   A Inicialização de membros de um objeto descartável não deve ser feita no construtor de uma instrução using.  
  
-   Construtores de aninhamento que são protegidos somente por um manipulador de exceção.  Por exemplo,  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     faz com que CA2000 ocorra porque uma falha de compilação do objeto StreamReader pode levar ao objeto FileStream nunca ser fechado.  
  
-   Os objetos dinâmicos devem usar um objeto sombra para implementar o padrão da disposição de objetos IDisposable.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra a menos que você chamar um método no objeto que chama `Dispose`, como <xref:System.IO.Stream.Close%2A>, ou se o método que gerou o aviso retorna quebras automáticas de um objeto IDisposable o objeto.  
  
## Regras Relacionadas  
 [CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: não descartar objetos várias vezes](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## Exemplo  
 Se você estiver implementando um método que retorna um objeto descartável, use um bloco try\/finally sem um bloco catch para certificar\-se de que o objeto é descartado.  Usando um block try\/finally, você permite que exceções sejam levantadas no ponto de falha e certifica\-se de que o objeto seja descartado.  
  
 No método OpenPort1, a chamada para abrir o objeto SerialPort de ISerializable ou a chamada a SomeMethod podem falhar.  Um aviso CA2000 é gerado nesta implementação.  
  
 No método OpenPort2, dois objetos de SerialPort são declarados e definidos como null:  
  
-   `tempPort`, que é usado para testar se operações do método são bem\-sucedidas.  
  
-   `port`, que é usado para valores de retorno do método.  
  
 O `tempPort` é construído e aberto em um bloco `try`, e qualquer outro trabalho necessário é executada no mesmo bloco `try`.  No final do bloco `try`, a porta aberta é atribuída ao objeto `port` que será retornado e o objeto `tempPort` é definido como `null`.  
  
 O bloco `finally` verifica o valor de `tempPort`.  Se não for null, uma operação falhou no método, e `tempPort` é fechado para certificar\-se de que todos os recursos sejam liberados.  O objeto retornado da porta conterá o objeto aberto SerialPort se as operações de método obtiverem sucesso, ou serão null se uma operação falhar.  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## Exemplo  
 Por padrão, o compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tem todas as verificação dos operadores aritméticos para overflow.  Portanto, qualquer operação aritmética do Visual Basic pode acionar <xref:System.OverflowException>.  Isso pode levar às violações inesperados nas regras como CA2000.  Por exemplo, a função a seguir CreateReader1 gera uma violação CA2000 porque o compilador do Visual Basic está emitindo um overflow que verifica a instrução para a adição que pode lançar uma exceção que faz com que o StreamReader a não seja descartado.  
  
 Para corrigir isso, você pode desativar a emissão de verificação de overflow pelo compilador do Visual Basic em seu projeto ou você pode alterar o código como na função CreateReader2.  
  
 Para desativar a emissão de verificação de overflow, clique com o botão direito do mouse no nome do projeto no solution Explorer e clique **Propriedades**.  Clique **Compilar**, clique **Opções de Compilação Avançadas**, e então marcar **Remover verificação de overflow de inteiros**.  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## Consulte também  
 <xref:System.IDisposable>   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)