---
title: "Como: adicionar uma dependência a um pacote VSIX | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
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
ms.openlocfilehash: 578d7cb8bc648765da37692e75cd3e9d0a487c8d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: adicionar uma dependência a um pacote VSIX
Você pode configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estão presentes no computador de destino. Para fazer isso, inclua as dependências do VSIX para o arquivo source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para adicionar uma dependência  
  
1.  Abra o arquivo source.extension.vsixmanifest no **Design** exibição. Vá para o **dependências** guia e clique em **novo**.  
  
2.  Para adicionar uma extensão instalados: no **adicionar nova dependência** caixa de diálogo, selecione **instalado extensão** e, em seguida, para o **nome**, selecione uma extensão na lista.  
  
3.  Para adicionar outro VSIX que não está instalado:: no **adicionar nova dependência** caixa de diálogo, selecione **arquivo no sistema de arquivos** e, em seguida, usar o **procurar** para selecionar VSIX.  
  
## <a name="see-also"></a>Consulte também  
 [Referência da extensão do esquema 1.0 VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparando extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
