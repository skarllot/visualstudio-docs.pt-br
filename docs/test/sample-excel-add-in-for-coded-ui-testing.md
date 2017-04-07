---
title: Suplemento de exemplo do Excel para testes de IU codificados| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
ms.author: douge
manager: douge
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 52b0394f0e52b8b7b640611253dcef693b4eca3c
ms.lasthandoff: 02/22/2017

---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Complemento do Excel de amostra para testes de IU codificado
Este suplemento de exemplo para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] foi projetado especificamente para dar suporte a testes de IU codificados de planilhas do Excel que são registrados e executados no Visual Studio Enterprise. O suplemento é criado usando o Visual Studio Tools para Office.  
  
 Para obter mais informações sobre como criar um suplemento do Excel, consulte [Passo a passo: criando o primeiro suplemento do VSTO para Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) ou pesquise o MSDN em busca de "Suplemento do Excel".  
  
 Embora o suplemento do Excel não seja o assunto principal desta documentação da extensão de teste de IU codificado para Excel, alguns comentários podem ser úteis.  
  
 As partes importantes deste suplemento:  
  
-   Classe `ThisAddIn` – gerencia o canal de comunicação remota do .NET entre o `ExcelUICommunicator` e a [Extensão de teste de IU codificado de exemplo para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` – um certificado de segurança para testar o suplemento.  
  
-   Classe `ExcelUICommunicator` – essa classe implementa a interface `IExcelUICommunication`.  
  
## <a name="thisaddin-class"></a>Classe ThisAddIn  
 A maior parte dessa classe, na verdade, é gerada pelo Visual Studio Tools para Office no arquivo `ThisAddIn.Designer.cs` quando você cria o projeto de suplemento do Excel.  
  
 Os membros que você deve implementar são os manipuladores de eventos: `ThisAddIn_Startup()` e `ThisAddIn_Shutdown()`. Sua finalidade é inicializar ou fechar o canal de comunicação remota do .NET que é usado pelo `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Esse arquivo contém um certificado de segurança temporário que é gerado pelo Visual Studio Tools para Office e concederá permissão ao assembly do suplemento para operar no processo do Excel para testar o suplemento e a extensão. Você deve excluir esse certificado e crie um novo na guia **Assinatura** da janela **Propriedades** do projeto ou anexe seu próprio certificado de teste.  
  
## <a name="exceluicommunicator-class"></a>Classe ExcelUICommunicator  
 Essa classe implementa a interface `IExcelUITestCommunication` e obtém as informações de interface do usuário solicitadas do modelo de objeto do Excel. Para obter mais informações, consulte [Interface de comunicador do Excel de amostra](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Passo a passo: criando o primeiro suplemento do VSTO para Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Desenvolvimento do Office e do SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)

