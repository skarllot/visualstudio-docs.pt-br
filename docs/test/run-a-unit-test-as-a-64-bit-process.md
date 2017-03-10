---
title: "Executar um teste de unidade como um processo de 64 bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de unidade, criando"
  - "testes de unidade, executando"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "mlearned"
manager: "douge"
---
# Executar um teste de unidade como um processo de 64 bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você tiver um computador de 64 bits, você pode executar testes de unidade e informações de cobertura de código de captura como um processo de 64 bits.  
  
## Executando um teste de unidade como um processo de 64 bits  
  
#### Para executar um teste de unidade como um processo de 64 bits  
  
1.  Se seu código ou teste foram criados como \/x86 de 32 bits, mas agora você deseja executar o como um processo de 64 bits, recompilar\-lo como **Qualquer CPU**opcionalmente, ou como **de 64 bits**.  
  
    > [!TIP]
    >  Para a máxima flexibilidade, você deve compilar seus projetos de teste com a configuração **Qualquer CPU**.  Em seguida, você poderá executar os agentes de 32 bits e de 64 bits.  Não há nenhuma vantagem de compilar projetos de teste com a configuração de **64 bits**.  
  
2.  No menu do Visual Studio, escolha **Testar**, então, escolha **Configurações**e escolha **Arquitetura do Processador**.  Escolha **x64** para executar testes como um processo de 64 bits.  
  
     \- ou \-  
  
     Especifique `<TargetPlatform>x64</TargetPlatform>` em um arquivo de .runsettings.  Uma vantagem desse método é que você pode especificar grupos de configurações em arquivos e rapidamente na alternância entre diferentes configurações diferentes.  Você também pode copiar configurações entre soluções.  Para obter mais informações, consulte [Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## Consulte também  
 [Executar testes de unidade com o Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md)   
 [Teste de unidade de código](../test/unit-test-your-code.md)   
 [Especificando configurações de teste do Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)