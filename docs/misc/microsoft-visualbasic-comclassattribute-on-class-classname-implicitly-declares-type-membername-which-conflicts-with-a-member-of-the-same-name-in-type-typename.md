---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; na classe &#39;&lt; classname &gt;&#39; declara implicitamente &lt; tipo &gt; &#39;&lt; nome &gt;&#39;, que est&#225; em conflito com um membro do mesmo nome em &lt; tipo &gt; &#39;&lt; typename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; na classe &#39;&lt; classname &gt;&#39; declara implicitamente &lt; tipo &gt; &#39;&lt; nome &gt;&#39;, que est&#225; em conflito com um membro do mesmo nome em &lt; tipo &gt; &#39;&lt; typename &gt;&#39;
'Microsoft.VisualBasic.ComClassAttribute' na classe '\< classname \>' declara implicitamente \< tipo \> '\< nome \>', que está em conflito com um membro do mesmo nome em \< tipo \> '\< typename \>'. Use 'Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\)' para ocultar o nome na base de '\< typename \>'.  
  
 Uma classe usando um `COMClassAttribute` Bloco de atributo implicitamente define uma interface com o mesmo nome como um membro da classe base. Nessa situação, o nome da interface deve sombrear o membro da classe base.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42101  
  
### Para corrigir este erro  
  
1.  Se você pretende ocultar o membro da classe base, defina `InterfaceShadows:=True` no `ComClassAttribute` Bloco de atributo.  
  
2.  Se você não pretende ocultar o membro da classe base, altere o nome da classe.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Classe ComClassAttribute](http://msdn.microsoft.com/pt-br/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Propriedade InterfaceShadows](http://msdn.microsoft.com/pt-br/0fae25bd-e0ba-4755-a76c-3b526b1ac795)