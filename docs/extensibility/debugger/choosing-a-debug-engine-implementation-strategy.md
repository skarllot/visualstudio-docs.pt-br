---
title: "Escolhendo uma estratégia de implementação do mecanismo de depuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ecc0eed4561b48bd93897c137c6f04e4804b1f47
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Escolhendo uma estratégia de implementação do mecanismo de depuração
Use a arquitetura de tempo de execução para determinar a estratégia de implementação do mecanismo (DE) de depuração. O mecanismo de depuração pode ser criado no processo para o programa a ser depurado, no processo no Gerenciador de depuração do Visual Studio sessão (SDM) ou fora de processo para ambos. As diretrizes a seguir devem ajudá-lo a escolher entre essas três estratégias.  
  
## <a name="guidelines"></a>Diretrizes  
 Embora seja possível DE ser out-of-process para o SDM e o programa a ser depurado, normalmente há nenhum motivo para isso. Chamadas entre limites de processo são relativamente lentas.  
  
 Depurar mecanismos já são fornecidos para o ambiente de tempo de execução nativo do Win32 e o ambiente de tempo de execução de linguagem comum. Se for necessário substituir DE para qualquer um desses ambientes, você deve criar o DE processo com o SDM.  
  
 Caso contrário, você pode escolher entre a criação DE em processo para o SDM ou em processo para o programa a ser depurado. É importante considerar se o avaliador de expressão de precisa de acesso frequente para o armazenamento de símbolo de programa, e se o repositório de símbolos pode ser carregado na memória para acesso rápido. Além disso, considere o seguinte:  
  
-   Se não houver muitas chamadas entre o avaliador de expressão e o armazenamento de símbolo, ou se o repositório de símbolos pode ser lidos no espaço de memória do SDM, crie o DE em processo para o SDM. Você deve retornar o CLSID do mecanismo de depuração para o SDM quando ele se conecta ao seu programa. O SDM usa esse CLSID para criar uma instância no processo de.  
  
-   Se o DE deve chamar o programa para acessar o repositório de símbolos, crie o DE processo com o programa. Nesse caso, o programa cria a instância do DE.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
