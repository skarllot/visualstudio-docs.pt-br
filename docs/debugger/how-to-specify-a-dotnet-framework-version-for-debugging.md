---
title: "Como especificar uma vers&#227;o do .NET Framework para depura&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, especificando versão para depuração"
  - "depurando [Visual Studio], especificando versão do .NET Framework"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como especificar uma vers&#227;o do .NET Framework para depura&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O depurador do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] dá suporte a versões anteriores de depuração do Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bem como à versão atual.  Se você iniciar um aplicativo do Visual Studio, o depurador sempre poderá identificar a versão correta do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para o aplicativo que você está depurando.  Se o aplicativo já estiver em execução e você usar **Anexar a**, o depurador nem sempre pode conseguir identificar uma versão anterior do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Se isso ocorrer, você receberá uma mensagem de erro, que indica  
  
 O depurador fez uma suposição incorreta sobre a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que seu aplicativo usará.  
  
 Nesses casos raros, você pode definir uma chave do Registro para indicar ao depurador a versão a ser usada.  
  
### Para especificar uma versão do .NET Framework para depuração  
  
1.  Examine no diretório Windows\\Microsoft.NET\\Framework para localizar as versões do .NET Framework instaladas no computador.  Os números de versão devem ser semelhantes a:  
  
     `V1.1.4322`  
  
     Identifique o número de versão correta e anote.  
  
2.  Inicie o **Editor do Registro** \(regedit\).  
  
3.  Em **Editor do Registro**, abra a pasta HKEY\_LOCAL\_MACHINE.  
  
4.  Navegue até: HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     Se a chave não existir, clique com o botão direito do mouse em HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine, e clique **Nova Chave**.  Nomeie a nova chave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Depois de navegar até {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, examine a coluna **Nome** e localize a chave CLRVersionForDebugging.  
  
    1.  Se a chave não existir, clique com o botão direito do mouse em {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} e clique em **Novo Valor de Cadeia de Caracteres**.  Clique com o botão direito no novo valor de cadeia de caracteres, clique em **Renomear** e digite `CLRVersionForDebugging`.  
  
6.  Clique duas vezes em **CLRVersionForDebugging**.  
  
7.  Na caixa **Editar Cadeia de Caracteres**, digite o número da versão do .NET Framework na caixa **Valor**.  Por exemplo: V1.1.4322  
  
8.  Clique em **OK**.  
  
9. Feche o **Editor do Registro**.  
  
     Se você ainda receber uma mensagem de erro quando começar a depuração, verifique se inseriu o número de versão corretamente no Registro.  Além disso, verifique se está usando uma versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] com suporte pelo Visual Studio.  O depurador é compatível com a versão atual e a anterior do .NET Framework, mas não é compatível com versões futuras.  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)