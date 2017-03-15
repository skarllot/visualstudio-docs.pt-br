---
title: "Estendendo janelas de ferramenta | Microsoft Docs"
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
  - "ferramenta do Windows [Visual Studio SDK],"
  - "janelas de documento"
  - "janelas de ferramentas"
  - "documento do Windows [Visual Studio SDK],"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# Estendendo janelas de ferramenta
Janelas de ferramentas do Visual Studio são, em geral, janelas de somente leitura que não são baseados em arquivo. Nesse diferem de janelas de documento, quais arquivos são exibidos no modo de leitura \/ gravação. O **Toolbox**, **Solution Explorer**, **propriedades** janela, e **navegador da Web** são exemplos de janelas de ferramenta.  
  
 Todas as janelas de ferramenta no Visual Studio 2010 e versões posteriores são baseados no WPF. Em versões do Visual Studio antes do Visual Studio 2010, janelas de ferramentas eram baseados em Windows Forms. Windows com base em formulários do Windows ainda podem ser exibido, mas novas janelas de ferramenta devem ser baseado no WPF.  
  
## Conceitos básicos de janela de ferramenta  
 Para fornecer uma janela da ferramenta, você deve registrá\-lo com o Visual Studio e especifique seu tamanho e local padrão. Para obter mais informações, consulte [Janelas de ferramenta no registro](../extensibility/tool-windows-in-the-registry.md).  
  
 Janelas de ferramentas normalmente são criadas ou abertas clicando em um comando de menu. Para criar uma janela de ferramentas programaticamente, consulte [Abrindo uma janela de ferramentas programaticamente](../misc/opening-a-tool-window-programmatically.md).  
  
 Janelas de ferramenta são a única instância por padrão, que significa que apenas uma instância da janela de ferramenta pode ser aberto por vez. Depois que uma janela de ferramenta de instância única é aberta, ela permanecerá aberta até que o IDE seja fechado. Quando você clica no botão Fechar uma janela da ferramenta de instância única, altera somente sua visibilidade. Você também pode criar várias instâncias janelas de ferramentas, que várias instâncias da janela podem ser abertas simultaneamente. Consulte [Criando uma janela de ferramentas de várias instâncias](../extensibility/creating-a-multi-instance-tool-window.md) para obter mais informações.  
  
 Janelas de ferramentas podem ser encaixada, flutuante ou com guias na estrutura do documento. O quadro de janela de ferramenta é fornecido pelo IDE e é usado para controlar o tamanho, local, estado de encaixe e outras propriedades persistentes. O painel da janela de ferramenta exibe o conteúdo. O tamanho e local padrão se aplicam somente quando a janela da ferramenta é aberto pela primeira vez; Depois que o estado de janela de ferramenta é mantido.  
  
 Painéis de janela de ferramenta podem hospedar controles de usuário do WPF e barras de ferramentas de suporte. Você pode substituir o <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propriedade para retornar o identificador do controle hospedado.  
  
 Janelas de ferramenta podem ser *dinâmico* \(também conhecido como *automática visível*\). Janelas de ferramentas dinâmica são visíveis sempre que seu contexto de interface do usuário relacionado se aplica. O uso de visibilidade automática pode reduzir a desordem das janelas do IDE. Para obter mais informações, consulte [Abrindo uma janela de ferramenta dinâmica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Os VSPackages não são a única maneira de criar uma janela de ferramenta. Suplementos podem criar uma janela de ferramentas usando o modelo de automação do Visual Studio. Para obter mais informações, consulte [How to: Create and Control Tool Windows](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md).  
  
## Consulte também  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [Janelas de documento](../extensibility/internals/document-windows.md)   
 [Adicionando pesquisa a uma janela de ferramentas](../extensibility/adding-search-to-a-tool-window.md)