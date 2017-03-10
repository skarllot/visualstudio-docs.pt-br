---
title: "CA2102: capturar exce&#231;&#245;es que n&#227;o sejam CLSCompliant em manipuladores gerais | Microsoft Docs"
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
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: capturar exce&#231;&#245;es que n&#227;o sejam CLSCompliant em manipuladores gerais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um membro em um assembly que não é marcado com <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou está marcado `RuntimeCompatibility(WrapNonExceptionThrows = false)` contém um bloco de captura que trata <xref:System.Exception?displayProperty=fullName> e não contém imediatamente após um bloco geral de captura.  Esta regra ignora os assemblies de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  
  
## Descrição da Regra  
 Um bloco de captura que trata captura de <xref:System.Exception> todas as exceções de correspondência de CLS \(CLS\).  No entanto, não capturar exceções de correspondência de non\-CLS.  As exceções correspondentes de Non\-CLS podem ser geradas a partir do código nativo ou de código gerenciado que foi gerado por assembler de linguagem intermediária da Microsoft \(MSIL\).  Observe que os compiladores C\# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não permite que a non\-CLS as exceções lançadas sejam compatíveis e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não capturar exceções de correspondência de non\-CLS.  Se a intenção do bloco de captura é manipular todas as exceções, use a seguinte sintaxe geral do bloco de captura.  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` ou `catch(Object^) {}`  
  
 Uma exceção de correspondência de non\-CLS sem\-tratamento se torna um problema de segurança quando as permissões são permitidas previamente removidas no bloco de captura.  Como as exceções de correspondência de non\-CLS não são capturadas, um método mal\-intencionado que jogasse uma exceção de correspondência de non\-CLS pode executar com permissões elevadas.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra quando a intenção é capturar todas as exceções, substituir ou adicionar um bloco geral de captura ou marcar o assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Se as permissões são removidas no bloco de captura, duplica a funcionalidade no bloco geral de captura.  Se não for a intenção para manipular todas as exceções, substitua o bloco de captura que trata <xref:System.Exception> com blocos de try\/catch que manipulam exceção de tipos específicos.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o bloco try não contém nenhuma instrução que podem gerar uma exceção de correspondência de non\-CLS.  Como todo o modo nativo ou código gerenciado podem gerar uma exceção de correspondência de non\-CLS, isso requer o conhecimento de qualquer código que pode ser executado em todos os caminhos de código no bloco try.  Observe que as exceções de correspondência de non\-CLS não são lançadas por Common Language Runtime.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe de MSIL que gerou uma exceção de correspondência de non\-CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## Exemplo  
 O exemplo a seguir mostra um método que contém um bloco geral de captura que satisfaça a regra.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Criar os exemplos anteriores da seguinte maneira.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Regras Relacionadas  
 [CA1031: não capturar tipos de exceção gerais](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## Consulte também  
 [Exceções e manipulação de exceções](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/pt-br/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)