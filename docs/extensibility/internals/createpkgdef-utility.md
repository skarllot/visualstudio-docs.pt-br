---
title: "Utilitário de CreatePkgDef | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
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
ms.openlocfilehash: b557dd9f463d087e3ead939f8006de6a3fda8c88
ms.lasthandoff: 02/22/2017

---
# <a name="createpkgdef-utility"></a>Utilitário de CreatePkgDef
Usa um arquivo. dll para uma extensão do Visual Studio como um parâmetro e cria um arquivo pkgdef para acompanhar o. dll. O arquivo pkgdef contém todas as informações de outra forma seriam gravadas no registro do sistema quando a extensão é instalada.  
  
> [!NOTE]
>  A maioria dos modelos de projeto que estão incluídos no SDK do Visual Studio automaticamente cria arquivos. pkgdef como parte do processo de compilação. Este documento destina-se para aqueles que desejam criar pacotes manualmente ou converter pacotes existentes para usar implantação pkgdef.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 out =`FileName`  
 Necessário. Define o nome do arquivo de saída pkgdef para`FileName`.  
  
 /codebase  
 Opcional. Registro de forças com o utilitário de base de código.  
  
 /assembly  
 Registro de forças com o utilitário de Assembly.  
  
 `AssemblyPath`  
 O caminho do arquivo. dll do qual você deseja gerar o pkgdef.  
  
## <a name="remarks"></a>Comentários  
 Implantação de extensão usando arquivos. pkgdef substitui os requisitos de registro de versões anteriores do Visual Studio.  
  
 Os arquivos. pkgdef devem ser instalados em um dos seguintes locais: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou %vsinstalldir%\Common7\IDE\Extensions\\. Se a pasta de instalação é %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**. Se a pasta de instalação é %vsinstalldir%\Common7\IDE\Extensions\\, a extensão está habilitada por padrão.  
  
> [!NOTE]
>  O **extensões e atualizações** ferramenta não pode ser usada para acessar uma extensão, a menos que ele é instalado como parte de um pacote VSIX.  
  
## <a name="see-also"></a>Consulte também  
 [Utilitário de CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
