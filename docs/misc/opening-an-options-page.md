---
title: "Abrir uma p&#225;gina de op&#231;&#245;es | Microsoft Docs"
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
  - "Abra uma página de opções"
  - "Opções de ferramentas"
  - "página de opções"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Abrir uma p&#225;gina de op&#231;&#245;es
Você pode exibir uma página de opções por meio de programação para que os usuários do seu pacote podem configurá\-lo durante a instalação. Para alterar as configurações depois que o pacote está instalado, um usuário ainda poderá acessar a página de opções usando o **opções** caixa de diálogo.  
  
### Para exibir uma página de opções personalizadas  
  
1.  Crie uma página de opções. Para obter mais informações, consulte [Criando páginas de opções](../extensibility/internals/creating-options-pages.md).  
  
2.  Obter o <xref:System.Type> da página de opções, aplicando o `typeof` palavra\-chave para o nome da classe que define a página de opções.  
  
3.  Chamar o <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> método usando o <xref:System.Type> da página de opções como um parâmetro.  
  
     O exemplo a seguir exibe uma página de opções chamada **HelloWorldOptions**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### Para exibir uma página de opções definida pelo Visual Studio  
  
1.  Na subchave do registro HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\, localize o nó para a página de opções que você deseja exibir e, em seguida, copie o GUID, que é o valor da chave de página.  
  
2.  Criar um <xref:System.ComponentModel.Design.CommandID> instância que tem as constantes <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> e <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> como parâmetros.  
  
     Especifica o **opções** caixa de diálogo.  
  
3.  Chamar o <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> método usando a <xref:System.ComponentModel.Design.CommandID> instância e o GUID de cadeia de caracteres como parâmetros.  
  
     O exemplo a seguir exibe o **geral** guia o **Editor de texto** página de opções.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]