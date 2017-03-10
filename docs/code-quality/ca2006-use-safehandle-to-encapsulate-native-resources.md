---
title: "CA2006: use SafeHandle para encapsular recursos nativos | Microsoft Docs"
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
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2006: use SafeHandle para encapsular recursos nativos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|Categoria|Microsoft.Reliability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 O código gerenciado usa <xref:System.IntPtr> para acessar recursos nativos.  
  
## Descrição da Regra  
 O uso de `IntPtr` em código gerenciado pode indicar um problema potencial de segurança e à confiabilidade.  Todos os usos de `IntPtr` devem ser examinados para determinar se o uso de <xref:System.Runtime.InteropServices.SafeHandle> , ou uma tecnologia semelhante, são necessários em seu lugar.  Surgirão problemas se `IntPtr` representa algum recurso nativo, como a memória, um identificador de arquivo, ou um soquete, a partir do qual o código gerenciado é considerado possui.  Se o código gerenciado é o proprietário do recurso, também deverá libere os recursos nativos associados a ele, porque uma falha isso faz com que o escapamento de recursos.  
  
 Nesses cenários, os problemas de segurança ou confiabilidade também existirão se o acesso é permitido a `IntPtr` multi\-threaded e uma maneira de liberar o recurso que é representado por `IntPtr` é fornecida.  Esses problemas envolvem de reciclagem do valor de `IntPtr` na versão do recurso quando o uso simultâneo de recursos é feito em outro thread.  Isso pode causar as situações de competição onde um thread pode ler ou gravar os dados associados ao recurso errado.  Por exemplo, se seu tipo armazena um identificador de sistema operacional como `IntPtr` e permite que os usuários chame **Close** e qualquer outro método que usa esse identificador simultaneamente e sem qualquer tipo de sincronização, seu código tem um identificador que recicla o problema.  
  
 Esse identificador que recicla o problema pode causar corrompimento dos dados e, geralmente, uma vulnerabilidade de segurança.  `SafeHandle` e sua classe <xref:System.Runtime.InteropServices.CriticalHandle> irmão fornecem um mecanismo para encapsular um identificador nativo para um recurso de modo que esses problemas de threading possam ser evitados.  Além disso, você pode usar `SafeHandle` e sua classe `CriticalHandle` irmãos para outros problemas de threading, por exemplo, para controlar cuidadosamente o tempo de vida de objetos gerenciados que contêm uma cópia do identificador nativo em chamadas para os métodos nativos.  Nessa situação, muitas vezes você pode remover chamadas a `GC.KeepAlive`.  A sobrecarga de desempenho que você incorrem quando você usa `SafeHandle` e, em um nível menor, `CriticalHandle`, frequentemente podem ser reduzidos ao design cuidado.  
  
## Como Corrigir Violações  
 Uso de `IntPtr` de conversão a `SafeHandle` para gerenciar a segurança de acesso a recursos nativos.  Consulte o tópico de referência de <xref:System.Runtime.InteropServices.SafeHandle> para obter exemplos.  
  
## Quando Suprimir Alertas  
 Você não deve eliminar esse aviso.  
  
## Consulte também  
 <xref:System.IDisposable>