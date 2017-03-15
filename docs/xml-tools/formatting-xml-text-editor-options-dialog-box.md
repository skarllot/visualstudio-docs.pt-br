---
title: "Formatting, XML, Text Editor, Options Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Formatting, XML, Text Editor, Options Dialog Box
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta caixa de diálogo permite que você especifique as configurações de formatação para o editor XML.  Você pode acessar a caixa de diálogo **Opções** de menu de **Ferramentas** .  
  
> [!NOTE]
>  Essas configurações estão disponíveis quando você seleciona a pasta de **Editor de Texto** , a pasta de **XML** , e então a opção de **Formatação** da caixa de diálogo **Opções** .  
  
## Atributos  
 **Formatação manual de atributo de preserve**  
 Os atributos não são reformatados.  Esse é o padrão.  
  
> [!NOTE]
>  Se os atributos estão em várias linhas, o editor recua cada linha de atributos para coincidir com o recuo de elemento pai.  
  
 **Os atributos cada um em sua própria linha**  
 Alinha os segundos e atributos subsequentes verticalmente para coincidir com o recuo do primeiro atributo.  O texto a seguir XML é um exemplo de como os atributos seriam alinhados.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## Reformatação Automática  
 **Na pasta da área de transferência**  
 Reformatar o texto XML colado da área de transferência.  
  
 **Na conclusão de marca de fim**  
 Reformatar o elemento quando a marca de fim é concluída.  
  
## Conteúdo Misto  
 **Conteúdo misturado preserve por padrão**  
 Determina se o editor reformate conteúdo misturado.  Por padrão, o editor tenta reformatar conteúdo misturado, a não ser que quando o conteúdo for encontrado em um escopo de `xml:space="preserve"` .  
  
 Se um elemento contém uma mistura de texto e de marcação, os conteúdos são consideradas conteúdo misturado.  O código a seguir é um exemplo de um elemento com conteúdo misturado.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## Consulte também  
 [XML Document Properties, Properties Window](../xml-tools/xml-document-properties-properties-window.md)   
 [XML Editor Components](../xml-tools/xml-editor-components.md)