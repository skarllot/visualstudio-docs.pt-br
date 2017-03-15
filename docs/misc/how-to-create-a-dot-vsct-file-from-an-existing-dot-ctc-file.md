---
title: "Como: criar um. Arquivo VSCT de uma j&#225; existente. Arquivos CTC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Arquivos VSCT, criando com base em um arquivo .ctc"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Como: criar um. Arquivo VSCT de uma j&#225; existente. Arquivos CTC
Você pode criar um arquivo. VSCT baseado em XML de um arquivo de origem do comando tabela .ctc existente. Fazendo isso, você pode tirar proveito do novo com base em XML [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] formato de compilador comando tabela \(VSCT\).  
  
### Para criar um arquivo. VSCT do arquivo .ctc  
  
1.  Obtenha uma cópia da linguagem Perl.  
  
2.  Obtenha uma cópia do script Perl ConvertCTCToVSCT.pl, geralmente localizado no *\< caminho de instalação do SDK do Visual Studio \>*\\VisualStudioIntegration\\Tools\\bin pasta.  
  
3.  Obtenha uma cópia do arquivo de origem .ctc que você deseja converter.  
  
4.  Coloque os arquivos no mesmo diretório.  
  
5.  No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela de Prompt de comando, navegue até o diretório.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     onde PkgCmd.ctc é o nome do arquivo .ctc e PkgCmd.vsct é o nome do arquivo. VSCT que você deseja criar.  
  
     Isso cria um novo arquivo. VSCT XML comando tabela fonte. Você pode compilar o arquivo usando Vsct.exe, o compilador VSCT, como faria com qualquer outro arquivo. VSCT.  
  
    > [!NOTE]
    >  Você pode melhorar a legibilidade do arquivo. VSCT, reformatar os comentários XML.  
  
## Consulte também  
 [Como: criar um. Arquivo VSCT](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Tabela de comando do Visual Studio \(. Arquivos de VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)