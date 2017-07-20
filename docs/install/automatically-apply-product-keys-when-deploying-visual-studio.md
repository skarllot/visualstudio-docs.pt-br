---
title: "Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio
É possível aplicar a chave do produto (Product Key) de forma programática como parte de um script usado para automatizar a implantação do Visual Studio. Chaves do produto (Product Keys) podem ser definidas em um dispositivo de forma programática durante a instalação do Visual Studio ou após a conclusão de uma instalação.

## <a name="apply-the-license-after-installation"></a>Aplicar a licença após a instalação
 É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário `StorePID.exe` nos computadores de destino no modo sem confirmação. `StorePID.exe` é um utilitário instalado com o Visual Studio 2017 no seguinte local padrão: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Execute o `StorePID.exe` com privilégios elevados, usando um agente do System Center ou em um prompt de comando com privilégios elevados, seguido pela chave do produto (Product Key) (incluindo os traços) e o MPC (Código do Produto da Microsoft). Lembre-se de incluir os traços na chave do produto (Product Key).

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Essa é uma linha de comando de exemplo para aplicar a licença ao Visual Studio 2017 Enterprise, que tem um MPC de 08860, com uma chave do produto (Product Key) `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, supondo a instalação em um local padrão:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 A seguinte tabela lista os códigos MPC para cada edição do Visual Studio:

| Edição do Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Se `StorePID.exe` tiver aplicado com êxito a chave do produto, retornará um `%ERRORLEVEL%` de 0. Se encontrar erros, retornará um código dependendo da condição de erro:

| Erro                     | Código |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>Consulte também
 * [Instalar o Visual Studio](../install/install-visual-studio.md)
 * [Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

