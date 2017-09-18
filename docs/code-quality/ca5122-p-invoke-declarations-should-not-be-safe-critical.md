---
title: "CA5122: declara&#231;&#245;es P/Invoke n&#227;o devem ser cr&#237;ticas para seguran&#231;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA5122: declara&#231;&#245;es P/Invoke n&#227;o devem ser cr&#237;ticas para seguran&#231;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma declaração P\/Invoke foi marcada com <xref:System.Security.SecuritySafeCriticalAttribute>:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke  
   }  
  
```  
  
 Neste exemplo, `C.Beep(...)` foi marcado como um método crítico de segurança.  
  
## Descrição da Regra  
 Os métodos são marcados como SecuritySafeCritical quando executam uma operação confidencial de segurança, mas também são seguros para serem usados pelo código transparente.  Uma das regras básicas do modelo de transparência de segurança é que o código transparente nunca pode chamar diretamente o código nativo por P\/Invoke.  Por isso, a marcação de um P\/Invoke como crítico de segurança não permitirá que o código transparente o chame, e é enganosa na análise de segurança.  
  
## Como Corrigir Violações  
 Para tornar P\/Invoke disponível para o código transparente, exponha um método wrapper crítico de segurança para ele:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.