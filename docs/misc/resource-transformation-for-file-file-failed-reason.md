---
title: "Falha na transforma&#231;&#227;o de recurso para o arquivo &#39;arquivo&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Falha na transforma&#231;&#227;o de recurso para o arquivo &#39;arquivo&#39;. &lt;reason&gt;
Falha do processador de recursos usado para transformar arquivos. resx em arquivos. Resources binário.  O motivo específico \(se houver\) é acrescentado ao final da seqüência de caracteres.  O processo de compilação falhará se esse erro ocorre.  
  
 Este erro é provavelmente causado por um arquivo. resx inválida.  Por exemplo, o arquivo pode foram aberto e modificado em um editor de texto.  
  
 Se você receber um \<reason\> de "Item já foi adicionado.  Chave no dicionário: chave 'NewControlName. \< nome da propriedade \>' adicionada: 'Nomedocontrole. \< nome da propriedade \>', "Leia as seguintes etapas para reproduzir e corrigir o erro.  
  
### Para reproduzir este erro  
  
1.  Crie um novo aplicativo do Windows.  Por padrão, o Form1 é criado.  
  
2.  Sobre o  **modo** menu, clique em  **Propriedades**.  
  
3.  No  **Propriedades** janela, defina o  **Localizable** propriedade `True`.  
  
4.  No  **Propriedades** windows, clique em  **idioma**e defina o valor como "Japonês".  
  
5.  Do toolbox, arraste um botão no formulário.  
  
6.  Altere o nome do botão de "Button1" para "BUTTON1".  
  
7.  No menu **Build**, clique em **Build Solution**.  
  
### Para corrigir este erro  
  
1.  Sobre o  **arquivo** , aponte para  **Abrir**e clique em  **arquivo**.  
  
2.  Localize o arquivo Form1 e clique em  **OK**.  Form1 é exibida.  
  
3.  Localize os valores de chave originais e, em seguida, excluí\-los manualmente da lista de dados.  Por exemplo, você tem um botão chamado "Button1".  Modificar o nome do botão para "BUTTON1".  Os valores de chave para "Button1" e "BUTTON1" estão no Form1.  Remover todas as entradas de "Button1" e, em seguida, recrie o projeto.  
  
## Consulte também  
 [Resources in .Resx File Format](http://msdn.microsoft.com/pt-br/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [Tipos de arquivo e extensões de arquivo em Visual Basic e C\# Visual](http://msdn.microsoft.com/pt-br/f793852c-da06-4d52-a826-65f635844772)