---
title: "Aplicativos de servidor SDI | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicativos de servidor SDI"
  - "aplicativos de servidor SDI, depuração"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aplicativos de servidor SDI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você estiver depurando um aplicativo de servidor de SDI, deverá especificar `/Embedding` ou `/Automation` na propriedade **Argumentos de linha de comando** na caixa de diálogo Páginas de Propriedades de *Project* para projetos do C\/C\+\+, do C\# ou do Visual Basic.  
  
 Com esses argumentos de linha de comando, o depurador pode iniciar o aplicativo de servidor como se tivesse sido iniciado de um contêiner.  Iniciar o contêiner do Gerenciador de Programas ou do Gerenciador de Arquivos fará com que o contêiner use a instância do servidor iniciada no depurador.  
  
## Localizando a propriedade Argumentos de Linha de Comando  
 Para acessar a caixa de diálogo Páginas de Propriedades de *Project*, clique com o botão direito do mouse no Gerenciador de Soluções e escolha Propriedades no menu de atalho.  Para localizar a propriedade Argumentos de linha de comando, expanda a categoria Propriedades de Configuração e clique na página Depuração.  
  
## Consulte também  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Como depurar servidores COM](../Topic/How%20to:%20Debug%20COM%20Servers.md)