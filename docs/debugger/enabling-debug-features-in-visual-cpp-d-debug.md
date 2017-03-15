---
title: "Habilitando recursos de depura&#231;&#227;o no Visual C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Opção de compilador /D_DEBUG (C++)"
  - "Macro _DEBUG"
  - "declarações, habilitando recursos de depuração"
  - "Opção de compilador D_DEBUG"
  - "depurar compilações, MFC"
  - "depurando [C++], habilitando recursos de depuração"
  - "depuração [MFC], habilitando recursos de depuração"
  - "Bibliotecas MFC, versão de depuração"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Habilitando recursos de depura&#231;&#227;o no Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], os recursos de depuração como asserções são habilitados quando você compila seu programa com o símbolo **\_DEBUG** definido.  Há duas maneiras de definir **\_DEBUG**:  
  
-   Especifique **\#define \_DEBUG** no código\-fonte ou  
  
-   Especifique a opção de compilador **\/D\_DEBUG**. \(Se você criar seu projeto no Visual Studio usando assistentes, **\/D\_DEBUG** será definido automaticamente na configuração Depuração\).  
  
 Quando **\_DEBUG** é definido, o compilador compila as seções de código cercadas por **\#ifdef \_DEBUG** e por `#endif`.  
  
 A configuração Depuração de um programa MFC deve ser vinculada a uma versão de depuração da biblioteca MFC.  Os arquivos de cabeçalho MFC determinam a versão correta deda biblioteca MFC à qual vincular com base nos símbolos definidos, como **\_DEBUG** e **\_UNICODE**.  Para obter detalhes, consulte [Versões da biblioteca MFC](/visual-cpp/mfc/mfc-library-versions).  
  
## Consulte também  
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)