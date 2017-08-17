---
title: Usar o Windows Runtime em JavaScript | Microsoft Docs
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="using-the-windows-runtime-in-javascript"></a>Usar o Windows Runtime em JavaScript
Ao gravar um aplicativo da UWP (Plataforma Universal do Windows), você pode usar classes, métodos e propriedades do Windows Runtime da mesma forma como usaria objetos, métodos e propriedades nativos do JavaScript. Este tópico fornece informações introdutórias e links a tópicos que explicam os conceitos básicos do uso das APIs do Tempo de Execução do Windows em JavaScript, inclusive uma explicação de como os tipos de Tempo de Execução do Windows são representados, como usar métodos assíncronos do Tempo de Execução do Windows e como ouvir e identificar eventos de Tempo de Execução do Windows.  
  
 Você pode encontrar documentação de referência de JavaScript em [Referência de linguagem JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Os recursos de Tempo de Execução do Windows não estão disponíveis para aplicativos executados no Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Documentação de referência do Tempo de Execução do Windows  
 Para documentação de referência, veja [Referência do Windows Runtime](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Os exemplos de código estão disponíveis em JavaScript e em C++, C# e Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Gravando componentes do Tempo de Execução do Windows em C++, C# ou Visual Basic  
 Para obter instruções e diretrizes para escrever componentes do Windows Runtime que podem ser consumidos em JavaScript, consulte [Criando componentes do Windows Runtime em C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) e [Criando componentes do Windows Runtime em C# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Convenções de uso de maiúsculas e minúsculas com recursos do Tempo de Execução do Windows  
 As convenções de uso de maiúsculas e minúsculas para recursos do Tempo de Execução do Windows em JavaScript são um pouco diferentes das convenções de outras linguagens:  
  
-   Os namespaces e as classes estão em Pascal:  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Os membros das classes, inclusive métodos e propriedades, além dos membros de estruturas e enumerações, estão em camel:  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Os nomes de eventos estão em minúsculas:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Considerações ao usar a API do Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Usar métodos assíncronos do Windows Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Manipular eventos do Windows Runtime em JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Representação em JavaScript de tipos do Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Projeção em JavaScript de DateTime e TimeSpan do Windows Runtime](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)
