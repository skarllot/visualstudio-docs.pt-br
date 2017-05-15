---
title: Como registrar e cancelar o registro VSPackages | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>VSPackages registrar e cancelar o registro
Usar atributos para registrar um VSPackage, mas  
  
## <a name="registering-a-vspackage"></a>Registrando um VSPackage  
 Você pode usar atributos para controlar o registro de VSPackages gerenciados. Todas as informações de registro estão contidas em um arquivo pkgdef. Para obter mais informações sobre o registro do arquivo, consulte [CreatePkgDef utilitário](../extensibility/internals/createpkgdef-utility.md).  
  
 O código a seguir mostra como usar os atributos padrão de registro para registrar o VSPackage.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Cancelando o registro de uma extensão  
 Se você estiver fazendo experiências com muita VSPackages diferentes e deseja removê-los da instância experimental, é possível executar o **redefinir** comando. Procure **redefinir a instância Experimental do Visual Studio** na página inicial do seu computador, ou execute este comando na linha de comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se você deseja desinstalar uma extensão que você instalou em sua instância de desenvolvimento do Visual Studio, vá para **ferramentas / extensões e atualizações**, localize a extensão e clique em **desinstalar**.  
  
 Se por algum motivo, nenhum desses métodos bem-sucedida em Desinstalando a extensão, você pode cancelar o registro do assembly de VSPackage da linha de comando da seguinte maneira:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
