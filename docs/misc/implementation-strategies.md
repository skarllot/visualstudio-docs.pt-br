---
title: "Estrat&#233;gias de implementa&#231;&#227;o | Microsoft Docs"
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
  - "VSPackages, estratégias de implementação"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Estrat&#233;gias de implementa&#231;&#227;o
Você pode estender o Visual Studio com partes do componente de automação suplementos, VSPackages, Managed Extensibility Framework \(MEF\) ou uma combinação dos três. Em geral, os suplementos são mais fáceis de desenvolver, mas são menos potente, que componentes VSPackages ou MEF. Os suplementos podem chamar interfaces de extensibilidade e VSPackages e componentes do MEF podem acessar o modelo de automação do Visual Studio. Você pode combinar várias abordagens diferentes para criar uma solução efetiva.  
  
 Os VSPackages podem ser escritos em código gerenciado ou não gerenciado. É recomendável que você escrever novo VSPackages em código gerenciado usando a estrutura de pacote gerenciado \(MPF\). Quase tudo o que pode ser escrito em código não gerenciado pode ser implementado mais fácil e segura em código gerenciado. No entanto, os aplicativos herdados escritos em código não gerenciado continuará a executar no Visual Studio.  
  
 Extensões simples adicionar janelas de ferramenta ou enviar informações para elementos de IU do Visual Studio, como a barra de status ou janela de saída. Aplicativos mais complexos podem ser gravados como hierarquias do Visual Studio, como o Gerenciador de servidores. Ainda mais energia pode ser obtida com a implementação de um projeto, editor ou designer. Por exemplo, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] se são implementados como serviços de linguagem.  
  
## Seções relacionadas  
 [SDK do Visual Studio e automação](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Discute o uso de automação, VSPackages ou uma combinação para criar aplicativos de extensibilidade do Visual Studio.  
  
 [SDK do Visual Studio e o código gerenciado](/visual-cpp/misc/visual-studio-sdk-and-managed-code)  
 Compara as diferentes maneiras de escrever um VSPackage no código gerenciado.  
  
 [Conceitos do Visual Studio IDE](/visual-cpp/misc/visual-studio-ide-concepts)  
 Discute os fundamentos de VSPackages e como usar um serviço.  
  
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Discute comuns elementos do aplicativo da interface do usuário no Visual Studio, como as janelas de Status e a saída.  
  
 [Hierarquias no Visual Studio](../extensibility/internals/hierarchies-in-visual-studio.md)  
 Fornece uma visão geral das hierarquias do Visual Studio, que aparecem no ambiente de desenvolvimento integrado \(IDE\) como árvores de nós.  
  
 [Projetos](../extensibility/internals/projects.md)  
 Fornece uma visão geral das classes do projeto e solução.  
  
 [Editor e extensões do serviço de linguagem](../extensibility/editor-and-language-service-extensions.md)  
 Mostra como estender o editor de código e texto e como criar designers e editores personalizados.  
  
 [Extensibilidade de serviço de linguagem herdada](../extensibility/internals/legacy-language-service-extensibility.md)  
 Mostra como criar serviços de linguagem.  
  
 [Referência SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Documentação de referência para o VSSDK.  
  
## Consulte também  
 [Começando a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md)