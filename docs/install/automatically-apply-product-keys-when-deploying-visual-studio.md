---
title: "Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: 1d1e0c656b91049ce53456e6c5c011c08ca2e58e
ms.openlocfilehash: db051eaf8ef98928c0fec858e4cc9380a3b7687b
ms.lasthandoff: 03/11/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio
É possível aplicar a chave do produto (Product Key) de forma programática como parte de um script usado para automatizar a implantação do Visual Studio. Chaves do produto (Product Keys) podem ser definidas em um dispositivo de forma programática durante a instalação do Visual Studio ou após a conclusão de uma instalação.  
  
## <a name="apply-the-license-during-installation"></a>Aplicar a licença durante a instalação  
 Use o parâmetro --productKey para aplicar uma chave do produto (Product Key) durante o processo de instalação do Visual Studio. Esse parâmetro de instalação pode ser usado com o parâmetro --quiet para instalar o Visual Studio em um estado já licenciado de um usuário final. Para usar o parâmetro --productKey, abra um prompt de comando. Execute o programa de instalação (por exemplo, vs_enterprise.exe ou vs_professional.exe) e defina o parâmetro --productKey com uma chave do produto (Product Key) (25 caracteres) com ou sem os traços:  
  
 Este é um comando de exemplo para a instalação do Visual Studio 2015 Enterprise com a chave do produto (Product Key) AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Aplicar a licença após a instalação  
 É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário storePID.exe nos computadores de destino no modo sem confirmação. StorePID.exe é um programa utilitário que é instalado com o Visual Studio em **\<drive>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**.  
  
 Execute o storePID.exe com privilégios elevados, usando um agente do System Center ou em um prompt de comandos com privilégios elevados, seguido pela chave do produto (Product Key) (incluindo os traços) e o MPC (Código do Produto da Microsoft). Lembre-se de incluir os traços na chave do produto (Product Key).  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Esta é uma linha de comando de exemplo para a instalação do Visual Studio 2017 Enterprise, que tem o MPC 08860, com uma chave do produto (Product Key) “AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE”:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  
  
 A seguinte tabela lista os códigos MPC para cada edição do Visual Studio:  
  
|Edição do Visual Studio|MPC|  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866| 
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
Se o StorePID.exe aplicou a chave do produto (Product Key) com êxito, ele retornará 0. Se ele encontrar erros, retornará um número entre 1 e 6.  
  
## <a name="see-also"></a>Consulte também  
 [Instalar o Visual Studio](../install/install-visual-studio.md)
 [Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
