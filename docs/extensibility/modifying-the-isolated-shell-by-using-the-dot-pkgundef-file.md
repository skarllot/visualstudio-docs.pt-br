---
title: Modificando o Shell isolado usando o. Arquivo Pkgundef | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
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
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificando o Shell isolado usando o. Arquivo Pkgundef
Você pode modificar o arquivo .pkgundef para excluir as entradas de registro especificada de um aplicativo de shell isolado. Normalmente, a primeira vez que um aplicativo é iniciado em um computador, o shell do Visual Studio copia as entradas de registro existentes do Visual Studio à chave do registro raiz do aplicativo. Isso inclui todas as referências a VSPackages atualmente instalados.  
  
 Para excluir uma entrada de registro específico de um aplicativo de shell isolado, adicione o arquivo do aplicativo .pkgundef a chave do pacote, seguida pela entrada. Chaves e entradas são representadas assim como o arquivo pkgdef; ou seja, como [$RootKey$] ou [$ $RootKey\\*subchave*] e "*entrada*" =*valor*, onde *subchave* é a subchave para afetar, *entrada* é a entrada para remover, e *valor* seja `""` ou `dword:00000000`.  
  
 Para excluir várias entradas de uma chave do registro, apenas liste a chave de uma vez, seguido por uma linha para cada entrada a ser excluído.  
  
 Para excluir uma chave do registro inteiro de um aplicativo de shell isolado, adicione a chave para o arquivo de .pkgundef de aplicativo, mas não especificam quaisquer entradas de registro para essa chave.  
  
 Você pode adicionar comentários no arquivo .pkgundef. Um comentário de linha deve ter duas barras como os dois primeiros caracteres.  
  
 Por exemplo, para remover o **conectar-se ao banco de dados** e **conectar-se a fornecer r** comandos no **ferramentas** menu, você pode remover o comentário da linha:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e adicione a linha:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 arquivo de .pkgundef do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [GUIDs de pacote de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md)
