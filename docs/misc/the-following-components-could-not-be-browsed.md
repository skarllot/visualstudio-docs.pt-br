---
title: "N&#227;o foi poss&#237;vel procurar os seguintes componentes: | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel procurar os seguintes componentes:
Essa caixa de mensagem pode listar vários erros relacionados à caixa de diálogo seleção de componente e Pesquisador de objetos. Os erros a seguir estão alguns dos mais comuns.  
  
## Componente ou tipo de arquivo não pode ser exibido no Pesquisador de objetos.  
 Esse erro geralmente ocorre quando você especifica um nome de arquivo que não existe ou não é válido ou um arquivo que não pode ser navegado por meio do Pesquisador de objetos.  
  
#### Para corrigir este erro  
  
-   Verifique se o nome de arquivo especificado existe e é um componente navegável, como um assembly do .NET, a biblioteca de tipos COM ou um arquivo de origem do navegador.  
  
## Arquivo não é um componente .NET Framework ou COM válido.  
 Esse erro geralmente ocorre quando o componente especificado não é um assembly .NET Framework ou uma biblioteca de tipos COM.  
  
#### Para corrigir este erro  
  
-   Escolha um componente diferente para procurar.  
  
## Arquivo não pode ser registrado como um componente COM.  
 Esse erro geralmente ocorre quando a biblioteca de tipos para um componente COM não pode ser registrada. A biblioteca de tipos pode não existir ou pode estar corrompida.  
  
#### Para corrigir este erro  
  
-   Reinstale o componente e tente novamente.  
  
## Nenhuma biblioteca de tipos correspondente está registrada ou as informações registradas não são válidas.  
 A biblioteca de tipos que você especificou não existe mais ou não pode conter informações válidas.  
  
#### Para corrigir este erro  
  
-   Verifique se a biblioteca de tipos existe e está registrada corretamente.  
  
## Componentes necessários para procurar nas bibliotecas de tipos COM estão ausentes ou não está registrado corretamente.  
 O arquivo vstlbinf está ausente ou incorretamente registrado.  
  
#### Para corrigir esse problema  
  
1.  Localizar vstlbinf em seu computador e registrá\-lo usando regsvr32.exe.  
  
     – ou –  
  
2.  Se você não conseguir localizar vstlbinf em seu computador, reinstale este produto.  
  
## Consulte também  
 [Pesquisador de Objetos](http://msdn.microsoft.com/pt-br/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Editar caixa de diálogo Definir componente personalizado](http://msdn.microsoft.com/pt-br/dc995bd7-afbf-4389-ba1c-f377b677ded7)