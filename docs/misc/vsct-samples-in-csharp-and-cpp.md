---
title: "VSCT exemplos em c# e C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Arquivos VSCT, exemplos"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# VSCT exemplos em c# e C++
VSCT tornou\-se a nova maneira de definir os comandos.  Dessa forma, uma alteração ocorreu como as amostras VSCT são compiladas em C\# e C\+\+.  Comandos agora são definidos em C\+\+ com arquivos externos e em C\# com uma seção de símbolos no arquivo .vsct.  
  
## Definindo comandos  
  
### Arquivos externos do C\+\+  
 Os exemplos de C\+\+, o compilador VSCT inclui arquivos externos para definir constantes usadas dentro das definições dos seus comandos.  A maneira de incluir esses arquivos e assim definir constantes nas definições dos seus comandos é adicionar um `Extern` marca dentro do arquivo .vsct e especifique o nome das referências de arquivo externo dentro do `href` atributo.  Esses arquivos são:  
  
-   GUIDs.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 O trecho de um arquivo de .vsct do C\+\+ a seguir demonstra como incluir esses arquivos:  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### Símbolos de C\#  
 Os exemplos de C\#, o arquivo de .vsct tem um `Symbols` seção no arquivo de si mesmo para definir comandos.  A definição de símbolos em um arquivo de .vsct em C\# origina\-se da maneira como as identificações dos elementos são definidas pela tabela de comandos.  Este é um trecho de um arquivo de .vsct C\# que especifica os comandos e constantes associados a eles:  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## A incorporação de Bitmaps  
  
### C\#  
 Bitmaps em C\+\+ e C\# CTO binários são armazenados externamente no disco.  A identificação de bitmap é definida de uma maneira para que a definição deve fornecer um atributo GUID para o bitmap, um `resID` atributo da faixa de bitmap que contém os bitmaps e, em seguida, as ids numéricas dos elementos usados dentro de uma definição de botão \(`usedList` atributo\).  Um aspecto importante dessa declaração é que o id do elemento deve ser o índice real \(baseado em 1\) do bitmap dentro da faixa de bitmap.  
  
 No exemplo a seguir uma faixa de bitmap é incluída que contém somente um elemento.  A identificação para este elemento é definida como guidMenuAndCommandsCmdSet:bmpArrow, portanto, o bmpArrow deve ser definido como 1.  Ele também é a declaração do bitmap.  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## Consulte também  
 [Tabela de comando do Visual Studio \(. Arquivos de VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)