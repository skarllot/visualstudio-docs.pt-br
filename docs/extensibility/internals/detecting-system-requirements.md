---
title: "Detecção de requisitos do sistema | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
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
ms.openlocfilehash: 014aef1a028b36840642ef44271495e156ba7ae2
ms.lasthandoff: 02/22/2017

---
# <a name="detecting-system-requirements"></a>Detecção de requisitos do sistema
Um VSPackage não funcionará a menos que o Visual Studio está instalado. Quando você usa o Microsoft Windows Installer para gerenciar a instalação de seu VSPackage, você pode configurar o instalador para detectar se o Visual Studio está instalado. Você também pode configurar para verificar o sistema para outros requisitos, por exemplo, uma versão específica do Windows ou uma determinada quantidade de RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Detecção de edições do Visual Studio  
 Para determinar se uma edição do Visual Studio está instalada, verifique se o valor da chave do registro de instalação (REG_DWORD) 1 na pasta apropriada, conforme listado na tabela a seguir. Observe que há uma hierarquia de edições do Visual Studio:  
  
1.  Empresa  
  
2.  Professional  
  
3.  Comunidade  
  
 Quando uma edição "superior" é instalada, as chaves do registro para edição, bem como para edições "inferiores" são adicionadas. Ou seja, se a Enterprise edition estiver instalada, a chave de instalação é definida como 1 para a empresa, bem como para as edições Professional e comunidade. Portanto, você precisa verificar somente para a edição de "melhor" você precisa.  
  
> [!NOTE]
>  Na versão de 64 bits do editor do registro, chaves de 32 bits são exibidas em HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. As chaves do Visual Studio estão sob HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produto|Chave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrado e isolado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Detectar quando o Visual Studio está em execução  
 O VSPackage não pode ser registrado corretamente se estiver executando o Visual Studio quando o VSPackage é instalado. O instalador deve detectar quando o Visual Studio está em execução e, em seguida, se recusará a usar o programa. Windows Installer não permite que você use entradas de tabela para habilitar essa detecção. Em vez disso, você deve criar uma ação personalizada, da seguinte maneira: Use o `EnumProcesses` função para detectar o processo de devenv.exe e, em seguida, defina uma propriedade de instalador que é usada em uma condição de início ou condicionalmente exibir uma caixa de diálogo que solicita ao usuário para fechar o Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
