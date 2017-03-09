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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: f96040d6e0a652998cc5603b67afbb564d81a8fd
ms.lasthandoff: 02/22/2017

---
# <a name="hosting-process-vshostexe"></a>Processo de hospedagem (vshost.exe)
O processo de hospedagem é um recurso do Visual Studio que melhora o desempenho de depuração, habilita a depuração de confiança parcial e habilita a avaliação de expressão em tempo de design. Os arquivos do processo de hospedagem contêm vshost no nome do arquivo e são colocados na pasta de saída do projeto. Para obter mais informações, consulte [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Arquivos do processo de hospedagem (.vshost.exe) são para uso do Visual Studio e não devem ser executados diretamente ou implantados com o aplicativo.  
  
## <a name="improved-debugging-performance"></a>Melhor desempenho de depuração  
 O processo de hospedagem cria um domínio do aplicativo e associa o depurador ao aplicativo. A execução dessas tarefas pode introduzir um atraso notável entre o tempo de início da depuração e o tempo do início da execução do aplicativo. O processo de hospedagem ajuda a melhorar o desempenho criando o domínio do aplicativo, associando o depurador na tela de fundo e salvando o domínio do aplicativo e o estado do depurador entre execuções do aplicativo. Para obter mais informações sobre domínios do aplicativo, consulte [Domínios do aplicativo](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Depuração de relação de confiança parcial  
 Um aplicativo pode ser especificado como um aplicativo de relação de confiança parcial na [página Segurança](../ide/reference/security-page-project-designer.md) do **Designer de Projeto**. A depuração de um aplicativo de relação de confiança parcial exige uma inicialização especial do domínio do aplicativo. Essa inicialização é manipulada pelo processo de hospedagem.  
  
## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design  
 A avaliação de expressão em tempo de design permite testar o código na janela **Imediata** sem a necessidade de executar o aplicativo. O processo de hospedagem executa esse código durante a avaliação da expressão em tempo de design. Para obter mais informações, consulte [Janela Imediata](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md)   
 [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md)   
 [Janela Imediata](../ide/reference/immediate-window.md)   
 [Domínios do aplicativo](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
