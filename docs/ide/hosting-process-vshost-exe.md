---
title: Processo de hospedagem (vshost.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 96cd56eaeea20b2b0defcb60a188c9e13c19ec6a
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# Processo de hospedagem (vshost.exe)
<a id="hosting-process-vshostexe" class="xliff"></a>
O processo de hospedagem é um recurso do Visual Studio que melhora o desempenho de depuração, habilita a depuração de confiança parcial e habilita a avaliação de expressão em tempo de design. Os arquivos do processo de hospedagem contêm vshost no nome do arquivo e são colocados na pasta de saída do projeto. Para obter mais informações, consulte [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Arquivos do processo de hospedagem (.vshost.exe) são para uso do Visual Studio e não devem ser executados diretamente ou implantados com o aplicativo.  
  
## Melhor desempenho de depuração
<a id="improved-debugging-performance" class="xliff"></a>  
 O processo de hospedagem cria um domínio do aplicativo e associa o depurador ao aplicativo. A execução dessas tarefas pode introduzir um atraso notável entre o tempo de início da depuração e o tempo do início da execução do aplicativo. O processo de hospedagem ajuda a melhorar o desempenho criando o domínio do aplicativo, associando o depurador na tela de fundo e salvando o domínio do aplicativo e o estado do depurador entre execuções do aplicativo. Para obter mais informações sobre domínios do aplicativo, consulte [Domínios do aplicativo](/dotnet/framework/app-domains/application-domains).  
  
## Depuração de relação de confiança parcial
<a id="partial-trust-debugging" class="xliff"></a>  
 Um aplicativo pode ser especificado como um aplicativo de relação de confiança parcial na [página Segurança](../ide/reference/security-page-project-designer.md) do **Designer de Projeto**. A depuração de um aplicativo de relação de confiança parcial exige uma inicialização especial do domínio do aplicativo. Essa inicialização é manipulada pelo processo de hospedagem.  
  
## Avaliação de expressão de tempo de design
<a id="design-time-expression-evaluation" class="xliff"></a>  
 A avaliação de expressão em tempo de design permite testar o código na janela **Imediata** sem a necessidade de executar o aplicativo. O processo de hospedagem executa esse código durante a avaliação da expressão em tempo de design. Para obter mais informações, consulte [Janela Imediata](../ide/reference/immediate-window.md).  
  
## Consulte também
<a id="see-also" class="xliff"></a>  
 [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md)   
 [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md)   
 [Janela Imediata](../ide/reference/immediate-window.md)   
 [Domínios do aplicativo](/dotnet/framework/app-domains/application-domains)
