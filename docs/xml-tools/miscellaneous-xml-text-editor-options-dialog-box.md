---
title: "Miscellaneous, XML, Text Editor, Options Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Miscellaneous, XML, Text Editor, Options Dialog Box
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta caixa de diálogo permite que você altere a automático e as configurações de esquema para o editor XML.  Você pode acessar a caixa de diálogo **Opções** de menu de **Ferramentas** .  
  
> [!NOTE]
>  Essas configurações estão disponíveis quando você seleciona a pasta de **Editor de Texto** , a pasta de **XML** , e então a opção de **Diversos** da caixa de diálogo **Opções** .  
  
## AutoInserção  
 **Fechar marcas**  
 Se a configuração de AutoCompletar estiver marcada, o editor adiciona automaticamente uma marca de fim quando você digita um sinal de maior \(\>\) para fechar uma tag de início, se a marca já não estiver fechada.  Este é o comportamento padrão.  
  
 A conclusão de um elemento vazio não depende da configuração de autocompletar.  Você sempre pode autocomplete um elemento vazio digitando uma barra invertida \(\/\).  
  
 **Aspas de atributo**  
 Ao criar atributos XML, o editor insere o caracteres de `=" "` e posiciona o acento circunflexo \(^\) dentro de aspas duplas.  
  
 Selecionado por padrão.  
  
 **Declarações de namespace**  
 O editor inserir automaticamente declarações namespace onde quer que são necessárias.  
  
 Selecionado por padrão.  
  
 **Outra marcação \(comentários, CDATA\)**  
 Comentários, CDATA, DOCTYPE, as instruções de processamento, e a outra marcação automática são concluídos.  
  
 Selecionado por padrão.  
  
## Rede  
 **Automaticamente os DTDs download e esquemas**  
 Os esquemas e as definições de tipo \(DTDs\) de documentos são baixados automaticamente locais HTTP.  Este recurso usa System.Net com a detecção automática do servidor de proxy ativada.  
  
 Selecionado por padrão.  
  
## Estrutura de tópicos  
 **Entre no modo estrutura de tópicos quando os arquivos abrem**  
 Ativa o recurso de estruturação quando um arquivo é aberto.  
  
 Selecionado por padrão.  
  
## Cache  
 **Esquemas**  
 Especifica o local do cache de esquema.  O botão procurar \(**...**\) abre a caixa de diálogo **Procura de Diretório** no local atual do cache de esquema.  Você pode selecionar um diretório diferente, ou você pode selecionar uma pasta na caixa de diálogo, clique com o botão direito do mouse, e escolha **Abrir** para ver o que está no diretório.  
  
## Consulte também  
 [XML Document Properties, Properties Window](../xml-tools/xml-document-properties-properties-window.md)   
 [XML Editor Components](../xml-tools/xml-editor-components.md)