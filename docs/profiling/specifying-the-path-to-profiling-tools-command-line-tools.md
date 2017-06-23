---
title: "Especificando o caminho para ferramentas de linha de comando de ferramentas de criação de perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e01fc9e6a23694b4e597c2d918b63a18697796ae
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Especificando o demarcador para ferramentas de linha de comando de ferramentas de criação de perfil
O caminho das ferramentas de linha de comando das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não é adicionado à variável de ambiente PATH. Em computadores de 32 bits, as ferramentas permanecem em um único diretório. Existem versões de 32 e 64 bits das ferramentas de criação de perfil em computadores de 64 bits.  
  
## <a name="32-bit-computers"></a>Computadores 32 bits  
 Em computadores de 32 bits, o diretório das ferramentas de criador de perfil padrão é *Unidade*Arquivos de Programas\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Computadores de 64 bits  
 Em computadores de 64 bits, especifique o caminho de acordo com a plataforma de destino do aplicativo cujo perfil foi criado.  
  
-   No caso de aplicativos de 32 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*Arquivos de Programas (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   No caso de aplicativos de 64 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*\Arquivos de Programas (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64
