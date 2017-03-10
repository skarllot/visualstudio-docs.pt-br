---
title: "Estendendo testes de IU codificado e grava&#231;&#245;es de a&#231;&#227;o para dar suporte ao Microsoft Excel | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Estendendo testes de IU codificado e grava&#231;&#245;es de a&#231;&#227;o para dar suporte ao Microsoft Excel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A estrutura de teste para testes de UI codificados e gravações de ação não oferece suporte a todas as interfaces de usuário possíveis.  Ele pode não oferecer suporte a interface do usuário específica que você deseja testar.  Por exemplo, você não pode criar imediatamente um teste de IU codificado ou uma ação de gravação para um [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] planilha.  No entanto, você pode criar sua própria extensão para o framework de teste de IU codificado que oferecerá suporte a interface do usuário específica, tirando proveito da extensibilidade da estrutura de teste de IU codificada.  O tópico a seguir fornece um exemplo de como estender o framework para dar suporte à criação de testes de UI codificados e gravações de ação [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Para obter mais informações sobre as plataformas com suporte, consulte [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
 Esta seção apresenta uma extensão de teste da interface do usuário codificada que pode gravar e reproduzir testes de planilhas do Excel.  Cada parte da extensão é explicado nesta seção e os comentários do código para desenvolvedores que desejam criar esse uma extensão.  
  
 ![Arquitetura de teste de interface do usuário](../test/media/ui_testarch.png "UI\_TestArch")  
Visão geral da arquitetura  
  
## Baixe o exemplo  
 O exemplo consiste em quatro projetos a `CodedUIExtensibilitySample.sln` solução:  
  
-   CodedUIextensibilitySample  
  
-   ExcelCodedUIAddInHelper  
  
-   ExcelUICommunicationHelper  
  
-   SampleTestProject  
  
 Obter o exemplo deste [postagem de blog](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  O exemplo é destinado ao uso com o Microsoft Excel 2010.  O exemplo pode funcionar com outras versões do Microsoft Excel, mas não é suportado atualmente.  
  
## Detalhes sobre o exemplo  
 As seções a seguir fornecem informações sobre o exemplo e sua estrutura.  
  
### Suplemento do Microsoft Excel: ExcelCodedUIAddinHelper  
 Esse projeto inclui um suplemento que é executado no processo do Excel.  Consulte [Complemento do Excel de amostra para testes de IU codificado](../test/sample-excel-add-in-for-coded-ui-testing.md) para uma visão geral sobre o projeto de suplemento.  
  
 Para obter mais informações, consulte [Passo a passo: criando o primeiro suplemento do VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md).  
  
### Comunicação do Excel da interface do usuário: ExcelUIcommunicationHelper  
 Esse projeto inclui o `IExcelUICommunication` interface e as classes de informações que são usadas para passar dados entre o Excel e estrutura de testes de IU codificado.  Para obter mais informações, consulte [Interface de comunicador do Excel de amostra](../test/sample-excel-communicator-interface.md).  
  
### Com o código de extensão de teste de interface do usuário: CodedUIExentsibilitySample  
 Esse projeto inclui as classes personalizadas que são usadas em testes de uma planilha do Excel.  O código para cada uma dessas classes é bastante auto\-explicativo.  No entanto, fornecemos uma breve descrição de cada classe personalizada.  Para obter mais informações, consulte [Extensão de teste de IU codificado de amostra para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### Implantando o suplemento e extensão  
 Após criar todos os objetos e projetos, execute fornecidos `CopyDrop.bat` arquivo como administrador.  Esse arquivo copia o `ExcelCodedUIAddinHelper` arquivos DLL e PDB para:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", onde o número de versão pode ser 11.0, 12.0 etc com base em sua versão do Visual Studio.  
  
 O `ExcelUICommunicationHelper` arquivos DLL e PDB são copiados para `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.  
  
 Talvez seja necessário ajustar os caminhos de cópia exata, mas nenhuma instalação adicional é necessária.  Em uma máquina de 64 bits, use o prompt de comando do Visual Studio Enterprise de 32 bits para executar o `CopyDrop.bat` arquivo.  
  
### Teste o Excel com o SampleTestProject  
 Você pode executar o teste no projeto de teste fornecido que usa uma versão específica do Excel que você não tenha, ou crie seu próprio projeto de teste e gravar um teste de sua preferência.  Para obter mais informações, consulte [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Práticas recomendadas para testes de IU codificados](../test/best-practices-for-coded-ui-tests.md)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)