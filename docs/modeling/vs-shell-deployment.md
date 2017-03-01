---
title: "Implantação do VS Shell | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e7632b99d3fa9d347b5a259cd446edc2f6d9efa8
ms.lasthandoff: 02/22/2017

---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell
Um shell isolado permite que você determine qual Visual Studio funcionalidade que você precisa para interagir com sua linguagem específica do domínio e como essa solução deve aparecer. Para obter mais informações sobre o shell do Visual Studio isolada, consulte [personalizar o Shell isolado](../extensibility/customizing-the-isolated-shell.md). Você pode encontrar mais informações sobre como personalizar o shell isolado no [personalizar o Shell isolado](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para definir um Shell do Visual Studio como o destino da implantação  
  
1.  No **DslPackage** projeto, abra **source.extension.tt**.  
  
2.  Em `<SupportedProducts>` inserir:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Substitua *MyIsolatedShell* com o nome do seu pacote de shell isolado.
