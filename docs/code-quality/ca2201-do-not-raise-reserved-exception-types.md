---
title: "CA2201: n&#227;o acionar tipos de exce&#231;&#227;o reservados | Microsoft Docs"
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
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201: n&#227;o acionar tipos de exce&#231;&#227;o reservados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método gerencie um tipo de exceção que sejam muito geral ou que é reservado em tempo de execução.  
  
## Descrição da Regra  
 Os seguintes tipos de exceção são muito gerais fornecer informações suficientes para o usuário:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Os seguintes tipos de exceção são reservados e devem ser descartados somente por Common Language Runtime:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Não gerencie exceções gerais**  
  
 Se você gerou um tipo de exceção geral, como <xref:System.Exception> ou <xref:System.SystemException> em uma biblioteca ou em uma estrutura, força consumidores para capturar todas as exceções, incluindo as exceções desconhecidas que não reconhecem a ser identificado.  
  
 Em vez disso, um ou outro geram um tipo mais derivada que já existe na estrutura, ou criar seu próprio tipo que deriva de <xref:System.Exception>.  
  
 **Exceções específicas de lançamento**  
  
 A tabela a seguir mostra os parâmetros e que exceções para gerar ao validar o parâmetro, incluindo o parâmetro de valor no acessador set de uma propriedade:  
  
|Descrição do parâmetro|Exceção|  
|----------------------------|-------------|  
|referência de`null`|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Fora do intervalo de valores permitido \(como um índice para uma coleção ou lista\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Valor inválido de `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contém um formato que não atende as especificações de parâmetro de um método \(como a cadeia de caracteres de formato para `ToString(String)`\)|<xref:System.FormatException?displayProperty=fullName>|  
|Se não inválido|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Quando uma operação não é válida para o estado atual do lançamento do objeto <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Quando uma operação é executada em um objeto que geram é descartado  <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Quando uma operação não é \(como em **Stream.Write** substituído em um fluxo aberto para leitura\) geram suporte <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Quando uma conversão resultaria em um lançamento <xref:System.OverflowException?displayProperty=fullName>de estouro \(como em uma sobrecarga explícita do operador cast\)  
  
 Para todas situações restantes, considere criar seu próprio tipo que deriva de <xref:System.Exception> e lançamento do.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o tipo de exceção lançada para um tipo específico que não seja um dos tipos permitidos.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Regras Relacionadas  
 [CA1031: não capturar tipos de exceção gerais](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)