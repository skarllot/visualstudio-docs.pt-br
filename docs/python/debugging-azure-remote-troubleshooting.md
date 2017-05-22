---
title: "Solução de problemas de depuração remota do Azure para Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: f9d9d1bc974e43cdd7d1da2a1468a9b7ef84f44b
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Solução de problemas da depuração remota para o Python e o Azure

O Visual Studio não conseguirá se anexar a um [Serviço de Aplicativo do Azure para depuração remota](debugging-azure-remote.md) por um dos seguintes motivos:

| Motivo | Resolução |
| --- | --- |
| Você não tem o Visual Studio 2013 Atualização 4 ou posterior instalado. | Instale uma versão adequada de [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| O projeto implantado no Serviço de Aplicativo não corresponde ao que está aberto no Visual Studio. | Carregue o projeto correto no Visual Studio. |
| O projeto não foi implantado com a configuração Depuração. | Reimplante o aplicativo clicando com o botão direito do mouse no projeto, no Gerenciador de Soluções e selecionando **Publicar**. Na guia **Configurações**, verifique se **Depuração** é a configuração selecionada. |
| O Serviço de Aplicativo não está em execução. | Inicie-o no Gerenciador de Servidores do Visual Studio ou no portal do Azure. |
| O Serviço de Aplicativo não está configurado para soquetes da Web. | Acesse o [portal do Azure](https://portal.azure.com), navegue até o Serviço de Aplicativo, abra a folha **Configurações > Configurações de aplicativo**, defina **Configurações gerais > Soquetes da Web** como **Ativado** e selecione **Salvar**. (Observe que as opções **Depuração** mostradas nessa folha *não* se aplicam à depuração do Python.) |
| `web.debug.config` foi modificado para desabilitar o proxy de depuração. | Exclua o arquivo e republique o projeto no Serviço de Aplicativo; durante esse tempo, o Visual Studio recriará o arquivo. |

Confira também: 

- [Depuração remota do Azure para o Python](debugging-azure-remote.md)

