---
title: "Complemento do Excel de amostra para testes de IU codificado | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de IU codificados, Exemplo de complemento do Excel"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Complemento do Excel de amostra para testes de IU codificado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse exemplo Add\-In para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] foi projetado especificamente para suportar planilhas codificado testes de interface do usuário do Excel que são registradas e executadas no Visual Studio Enterprise. O suplemento é criado usando o Visual Studio Tools for Office.  
  
 Para obter mais informações sobre como criar um suplemento do Excel, consulte [Passo a passo: criando o primeiro suplemento do VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md) ou pesquisar o MSDN para "Excel Add\-In".  
  
 Embora o suplemento do Excel não seja o assunto principal desta documentação da extensão de teste de IU codificado para Excel, alguns comentários podem ser úteis.  
  
 As partes importantes do Add\-In:  
  
-   `ThisAddIn`  Classe \- gerencia o canal de comunicação remota .NET entre o `ExcelUICommunicator` e o [Extensão de teste de IU codificado de amostra para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  \-Um certificado de segurança para testar o suplemento.  
  
-   `ExcelUICommunicator`  Classe \- essa classe implementa o `IExcelUICommunication` interface.  
  
## Classe ThisAddIn  
 A maioria dessa classe, na verdade, gerado pelo Visual Studio Tools for Office no `ThisAddIn.Designer.cs` arquivo quando você criar o projeto de suplemento do Excel.  
  
 Os membros que você deve implementar são os manipuladores de eventos: `ThisAddIn_Startup()` e `ThisAddIn_Shutdown()`.  Sua finalidade é inicializar ou feche o canal de comunicação remota do .NET que é usado pelo `ExcelUICommunicator`.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Esse arquivo contém um certificado temporário que é gerado pelo Visual Studio Tools for Office e permitirá que o suplemento assembly para operar no processo do Excel para testar o suplemento e a extensão.  Você deve excluir esse certificado e crie um novo na **assinatura** guia do projeto **propriedades** janela, ou anexar seu próprio teste de certificado.  
  
## Classe ExcelUICommunicator  
 Essa classe implementa o `IExcelUITestCommunication` da interface e obtém as informações solicitadas da interface do usuário do modelo de objeto do Excel.  Para obter mais informações, consulte [Interface de comunicador do Excel de amostra](../test/sample-excel-communicator-interface.md).  
  
## Consulte também  
 [Estendendo testes de IU codificado e gravações de ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Passo a passo: criando o primeiro suplemento do VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Desenvolvimento do Office e do SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)