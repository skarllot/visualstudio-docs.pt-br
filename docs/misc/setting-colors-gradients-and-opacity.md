---
title: "Definindo cores, gradientes e opacidade | Microsoft Docs"
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
  - "Design de elemento de interface do usuário [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Definindo cores, gradientes e opacidade
Todos os elementos de interface de usuário no Visual Studio são criados no Windows Presentation Foundation \(WPF\). Portanto, quando você cria janelas de ferramentas ou outros elementos de interface do usuário, você pode aplicar cores, gradientes e opacidade definindo os atributos apropriados nesses elementos. Você pode defini\-los com valores específicos usando o **propriedades** janela, ou você pode consultar o ambiente de desenvolvimento integrado \(IDE\) para valores do sistema. É recomendável que você use valores de sistema quando você deseja que suas extensões para se parecer com o restante do IDE.  
  
 Interface de código nativo e interface do usuário do Windows Forms ainda são suportadas para compatibilidade com versões anteriores. Para obter informações sobre como definir cores e gradientes nas extensões não\-WPF, consulte o [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] documentação.  
  
## Definindo cores, gradientes e opacidade  
 Você pode definir alterar a aparência da maioria dos elementos XAML, definindo seus `Background`, `Foreground`, `Opacity`, ou outros atributos visuais. Esses atributos correspondem a propriedades que recebem um <xref:System.Windows.Media.Brush?displayProperty=fullName> como um valor.  
  
#### Para definir a opacidade, gradientes e cores de plano de fundo em uma janela de ferramenta  
  
1.  Abra MyControl.xaml.  
  
2.  No **XAML** painel, no nível superior <xref:System.Windows.Controls.UserControl> elemento, digite `background=`.  
  
     O IntelliSense exibe uma lista de cores para o atributo de plano de fundo.  
  
     Selecione uma cor na lista.  
  
3.  No **propriedades** janela, expanda o **pincéis** nó e clique **fundo**.  
  
     O **propriedades** janela exibe um selecionador de cores. Acima de cor seletor é uma linha de ícones que representam os pincéis.  
  
4.  Use os controles deslizantes para escolher uma cor.  
  
     O XAML imediatamente atualizado para mostrar a nova cor do plano de fundo.  
  
5.  Clique no ícone de pincel de gradiente.  
  
     O seletor de cores é alterado para um seletor de gradiente.  
  
6.  Use os controles deslizantes para escolher um gradiente.  
  
     O XAML é atualizada imediatamente para mostrar o novo plano de fundo gradiente.  
  
7.  Clique no ícone de pincel de imagem.  
  
     O seletor de gradiente muda para uma ferramenta de seleção de imagem.  
  
8.  Selecione uma imagem e definir seu Alongar e bloco de parâmetros.  
  
     O XAML imediatamente atualizado para mostrar a nova imagem de plano de fundo.  
  
9. Clique no ícone de pincel nulo.  
  
     Plano de fundo do designer retorna ao neutro e o `BackGround` atributo é definido como `"{x:Null}"`.  
  
## Consultar valores de sistema  
 Você pode consultar valores de sistema usando o <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName> classe propriedades, que se referem a pincéis que são definidas em outras partes do Visual Studio.  
  
#### Para definir cores, gradientes e opacidade consultando valores do sistema  
  
1.  Selecione um elemento XAML.  
  
2.  Na definição de elemento, defina um dos atributos do elemento visual a uma propriedade do `VsBrushes` de classe, conforme mostrado no exemplo a seguir.  
  
     [!CODE [TWShortcutMenu#32](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#32)]  
  
     Usando o [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) extensão permite que o valor alterar conforme necessário, por exemplo, quando um usuário altera as configurações. Você deve usar o [X:Static](../Topic/x:Static%20Markup%20Extension.md) extensão porque o `VsBrushes` classe não é parte do namespace do WPF padrão.  
  
## Consulte também  
 [Estendendo janelas de ferramenta](../misc/extending-tool-windows.md)