---
title: Solucionando problemas de registro de pacote RegPkg | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
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
ms.openlocfilehash: f0681fff9d54f83c9da8b9afb0ff533e076ad144
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-regpkg-package-registration"></a>Solucionando problemas de registro de pacote RegPkg
> [!NOTE]
>  É a melhor maneira de registrar pacotes no Visual Studio usando arquivos. pkgdef. Isso permite a implantação de extensão sem precisar acessar o registro do sistema. Pkgdef arquivos são criados usando o [CreatePkgDef utilitário](../../extensibility/internals/createpkgdef-utility.md).  
  
 Para registrar um pacote usando RegPkg em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve usar a versão de RegPkg apropriado para seu pacote.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versões RegPkg relacionadas às versões do pacote  
 Há duas versões do RegPkg. Uma versão é incluída no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Use esta versão para registrar os pacotes que foram criados usando um dos seguintes assemblies:  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Ele não pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll anterior.  
  
 A versão anterior do RegPkg pode registrar os pacotes que foram criados usando o assembly Microsoft.VisualStudio.Shell.dll. No entanto, ele não pode registrar pacotes criados usando versões mais recentes do assembly.  
  
## <a name="see-also"></a>Consulte também  
 [Liberar um produto](../../misc/releasing-a-visual-studio-integration-product.md)
