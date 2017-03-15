---
title: "Como: Cancelar o registro VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "a desinstalação de aplicativos de exemplo [Visual Studio SDK]"
  - "instalação, VSPackages"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Como: Cancelar o registro VSPackages
Por padrão, quando você cria os VSPackages, eles são registrados para o hive do registro experimental. O hive experimental pode preencher com VSPackages que você não deseja manter depois que você experimentou com eles.  
  
 Para excluir todos os pacotes que estão registrados no hive experimental, redefina o hive, usando a ferramenta CreateExpInstance com a opção \/Reset. Para obter mais informações, consulte [A instância Experimental](../extensibility/the-experimental-instance.md).  
  
## Cancelando o registro VSPackages individuais  
  
#### Para cancelar o registro de um VSPackage não gerenciado  
  
1.  Clique em **Iniciar**, clique em **executar**, tipo `regsvr32 /u` *pathToVSPackage.dll*, e, em seguida, clique em OK.  
  
 Como não gerenciados VSPackages contêm código de auto\-registro, você pode usar o utilitário regsvr32 para registrá\-los e cancelar seu registro.  
  
#### Para cancelar o registro de um VSPackage gerenciado  
  
1.  Clique em **Iniciar**, clique em **executar** tipo *caminho de instalação do SDK do Visual Studio*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll*, e, em seguida, clique em OK.  
  
 A ferramenta RegPkg lê os atributos do registro que podem ser inseridos em um VSPackage gerenciado. O **\/unregister** opção instrui RegPkg para remover as informações do registro.  
  
## Consulte também  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/pt-br/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)