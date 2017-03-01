---
title: "Usado em cadeias de substituição. Pkgdef e. Arquivos de Pkgundef | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Usado em cadeias de substituição. Pkgdef e. Arquivos de Pkgundef
Você pode usar as cadeias de caracteres de substituição listadas na pkgdef e arquivos .pkgundef definir para o Visual Studio isolados do aplicativo de shell.  
  
## <a name="substitution-strings"></a>Cadeias de caracteres de substituição  
  
|Cadeia de caracteres|Descrição|  
|------------|-----------------|  
|$=*RegistryEntry*$|O valor de *RegistryEntry* entrada. Se a cadeia de caracteres de entrada de registro termina em uma barra invertida (\\), então o valor padrão da subchave do registro é usado. Por exemplo, a substituição de cadeia de caracteres $= HKEY_CURRENT_USER\Environment\TEMP$ é expandido para a pasta temporária do usuário atual.|  
|$ $AppName|O nome qualificado do aplicativo que é passado para os pontos de entrada AppEnv.dll. O nome qualificado consiste no nome do aplicativo, um sublinhado e o identificador de classe (CLSID) do objeto de automação do aplicativo, que também é registrado como o valor da configuração ThisVersionDTECLSID no arquivo pkgdef do projeto.|  
|$AppDataLocalFolder|A subpasta % LOCALAPPDATA % para este aplicativo.|  
|$ $BaseInstallDir|O caminho completo do local onde o Visual Studio foi instalado.|  
|$ $CommonFiles|O valor da variável de ambiente % CommonProgramFiles %.|  
|$ $MyDocuments|O caminho completo da pasta Meus documentos do usuário atual.|  
|$ $PackageFolder|O caminho completo do diretório que contém os arquivos de assembly do pacote para o aplicativo.|  
|$ $ProgramFiles|O valor da variável de ambiente % ProgramFiles %.|  
|$ $RootFolder|O caminho completo do diretório raiz do aplicativo.|  
|$ $RootKey|A chave do registro raiz do aplicativo. Por padrão, a raiz é em HKEY_CURRENT_USER\\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* (quando o aplicativo é executado, _Config é anexado a essa chave). Ele é definido pelo valor RegistryRoot o *SolutionName*pkgdef.<br /><br /> A cadeia de caracteres de $ $RootKey pode ser usada para recuperar um valor do registro na subchave do aplicativo. Por exemplo, a cadeia de caracteres "$= $RootKey$ \AppIcon" retornará o valor da entrada AppIcon sob a subchave de raiz do aplicativo.<br /><br /> O analisador processa o arquivo pkgdef sequencialmente e pode acessar uma entrada de registro na subchave aplicativo somente se a entrada foi definida anteriormente|  
|$ $ShellFolder|O caminho completo do local onde o Visual Studio foi instalado.|  
|$ $System|A pasta Windows\system32.|  
|$ $WINDIR|A pasta do Windows.|  
  
 Se o analisador não reconhece a cadeia de caracteres de substituição ou não é possível determinar o valor de uma entrada de registro ou uma variável de ambiente, em seguida, ele não executa substituição dessa parte da cadeia de caracteres.
