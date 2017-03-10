---
title: "Especificando o caminho para ferramentas de linha de comando de ferramentas de cria&#231;&#227;o de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Especificando o caminho para ferramentas de linha de comando de ferramentas de cria&#231;&#227;o de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O caminho das ferramentas de linha de comando das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não é adicionado à variável de ambiente PATH.  Em computadores de 32 bits, as ferramentas permanecem em um único diretório.  Existem versões de 32 e 64 bits das ferramentas de criação de perfil em computadores de 64 bits.  
  
## Computadores 32 bits  
 Em computadores de 32 bits, o diretório das ferramentas de criação de perfil padrão é *Unidade*\\Arquivos de Programas\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools.  
  
## Computadores de 64 bits  
 Em computadores de 64 bits, especifique o caminho de acordo com a plataforma de destino do aplicativo cujo perfil foi criado.  
  
-   No caso de aplicativos de 32 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*\\Arquivos de Programas \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools  
  
-   No caso de aplicativos de 64 bits, o diretório padrão das ferramentas de criação de perfil é:  
  
     *Unidade*\\Arquivos de Programas \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools\\x64