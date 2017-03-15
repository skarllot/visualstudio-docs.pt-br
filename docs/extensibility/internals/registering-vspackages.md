---
title: Registrando os VSPackages | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 20
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
ms.openlocfilehash: b76ea797560ff71a4504dda401bac9aee9b6b20e
ms.lasthandoff: 02/22/2017

---
# <a name="registering-vspackages"></a>Registrando os VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se baseia em arquivos. pkgdef para descrever e localizar um VSPackage. Um arquivo pkgdef contém todas as informações de registro que caso contrário, seriam adicionadas ao registro do sistema. Os VSPackages gerenciados são registrados pelo adicionar atributos ao código-fonte e, em seguida, executar o [CreatePkgDef utilitário](../../extensibility/internals/createpkgdef-utility.md) do assembly resultante para gerar um arquivo pkgdef.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificando o local do arquivo de VSPackage ao Shell do VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Descreve o caminho de carregamento para VSPackages.  
  
 [VSPackages registrar e cancelar o registro](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica como registrar um VSPackage.  
  
 [Usando um atributo de registro personalizado para registrar uma extensão](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Descreve como criar um manifesto de registro que pode ser usado para implantar um VSPackage gerenciado.
