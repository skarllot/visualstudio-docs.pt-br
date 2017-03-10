---
title: "Erro MSB3152 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3152 (MSBuild)
**MSB3152: O local de instalação para os pré\-requisitos não foi definido como 'site do fornecedor de componentes' e o arquivo '\<file\> ' no item '\<package\> ' não pode ser localizado no disco.  Para obter mais informações, consulte a Ajuda.**  
  
 Este erro ocorre quando um arquivo que é necessário para o instalador de pré\-requisitos estiver ausente.  Os arquivos do installer entram em uma pasta especial que Visual Studio reservado para pacotes redistribuíveis.  A pasta varia de acordo com a versão do Visual Studio que você está desenvolvendo com.  Para obter mais informações sobre o local da pasta específica, consulte [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
### Para corrigir este erro  
  
-   Determine se o arquivo existe no disco.  
  
-   Use o HomeSite para tentar resolver o problema do pacote.  
  
-   Definir `CopyComponents` para `false` no arquivo de projeto.  
  
-   Não use o pacote de bootstrapper quebrado.  
  
## Consulte também  
 [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md)