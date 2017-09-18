---
title: "CA1901: as declara&#231;&#245;es de P/Invoke devem ser port&#225;teis | Microsoft Docs"
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
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1901: as declara&#231;&#245;es de P/Invoke devem ser port&#225;teis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Interromper \- se o P\/Invoke é visível fora do assembly.  Interrompendo não \- se o P\/Invoke não é visível fora do assembly.|  
  
## Causa  
 Esta regra avalia o tamanho de cada parâmetro e o valor de retorno de um P\/Invoke e verifique se seu tamanho, quando marshaling para código não gerenciado em plataformas de 32 bits e de 64 bits, está correto.  A violação mais comuns dessa regra é transmitir um inteiro fixa dimensionado onde um plataforma dependente, variável ponteiro\- dimensionado é necessário.  
  
## Descrição da Regra  
 Qualquer um dos seguintes cenários violar esta regra ocorre:  
  
-   O valor de retorno ou o parâmetro são digitados como um inteiro de tamanho fixo quando deve ser digitado como `IntPtr`.  
  
-   O valor de retorno ou o parâmetro são digitados como `IntPtr` quando devem ser digitados como um inteiro de tamanho fixo.  
  
## Como Corrigir Violações  
 Você pode corrigir essa violação usando `IntPtr` ou `UIntPtr` para representar os identificadores em vez de `Int32` ou de `UInt32`.  
  
## Quando Suprimir Alertas  
 Você não deve eliminar esse aviso.  
  
## Exemplo  
 O exemplo a seguir demonstra uma violação desta regra.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 Neste exemplo, o parâmetro de `nIconIndex` é declarado como `IntPtr`, que é de 4 bytes de comprimento em uma plataforma de 32 bits e 8 bytes de comprimento em uma plataforma de 64 bits.  Na declaração não gerenciados de forma, você pode ver que `nIconIndex` é um número inteiro sem sinal de 4 bytes em todas as plataformas.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Exemplo  
 Para corrigir a violação, altere a declaração ao seguinte:  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## Consulte também  
 [Avisos de portabilidade](../code-quality/portability-warnings.md)