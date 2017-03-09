---
title: Como desabilitar o processo de hospedagem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: aa9671e09f6751d51535be5343fe849293f23f16
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-disable-the-hosting-process"></a>Como desabilitar o processo de hospedagem
Chamadas para determinadas APIs podem ser afetadas quando o processo de hospedagem está habilitado. Nesses casos, é necessário desabilitar o processo de hospedagem para retornar os resultados corretos.  
  
### <a name="to-disable-the-hosting-process"></a>Para desabilitar o processo de hospedagem  
  
1.  Abra um projeto executável em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Projetos que não geram executáveis (por exemplo, projetos de serviço ou biblioteca de classes) não têm essa opção.  
  
2.  No menu **Projeto**, clique em **Propriedades**.  
  
3.  Clique na guia **Depurar**.  
  
4.  Desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.  
  
 Quando o processo de hospedagem é desabilitado, vários recursos de depuração ficam não disponíveis ou apresentam um desempenho reduzido. Para obter mais informações, consulte [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).  
  
 De modo geral, quando o processo de hospedagem está desabilitado:  
  
-   O tempo necessário para iniciar a depuração de aplicativos [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aumenta.  
  
-   A avaliação de expressões em tempo de design fica não disponível.  
  
-   A depuração de confiança parcial ficará não disponível.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md)   
 [Processo de hospedagem (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Compilações durante o desenvolvimento de aplicativos](http://msdn.microsoft.com/en-us/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
