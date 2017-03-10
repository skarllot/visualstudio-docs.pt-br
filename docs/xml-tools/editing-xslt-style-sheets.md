---
title: "Editing XSLT Style Sheets | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Editing XSLT Style Sheets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor XML pode ser usado para editar folhas de estilos XSLT.  Você pode tirar proveito dos recursos do editor padrão como o IntelliSense, estruturação, trechos XML, e assim por diante.  Além disso, há também os novos recursos que tornam ficar em XSLT.  
  
## Recursos de fonte  
 A tabela a seguir descreve os recursos específicos para trabalhar com folhas de estilos XSLT.  
  
 **Coloração de sintaxe**  
 Palavras\-chave XSLT, como `template`, `match`, são exibidos, e assim por diante na cor da palavra\-chave XSLT especificada pelas configurações de **Fontes e Cores** .  
  
 **Traços ondulados**  
 O editor XML usa o arquivo de xslt.xsd instalado para validar folhas de estilos XSLT.  Os erros de validação são mostrados como sublinhados ondulados azuis.  O editor XML também compila a folha de estilos em segundo plano e relatar erros ou avisos do compilador com traços ondulados apropriadas.  
  
 **Suporte para blocos de script**  
 O código nos blocos de script é suportado pelo depurador XSLT para que você pode definir pontos de interrupção e percorrer o código de bloco de script.  
  
 **Saída XSLT de exibição**  
 Você pode executar uma transformação XSL e exibir a saída do editor XML.  Para obter mais informações, consulte [How to: Execute an XSLT Transformation from the XML Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Depuração XSLT**  
 Você pode iniciar o depurador XSLT de um arquivo fonte no editor XML.  O depurador oferece suporte pontos de interrupção no arquivo XSLT, estado de configuração de execução XSLT de exibição, e assim por diante.  Passa sobre uma variável XSLT traz anterior um ToolTip com o valor da variável.  O depurador pode ser usado para depurar uma folha de estilos, ou depurar uma transformação XSL compilado chamada de outro aplicativo.  Para obter mais informações, consulte [Debugging XSLT](../xml-tools/debugging-xslt.md).  
  
## Consulte também  
 [XML Editor](../xml-tools/xml-editor.md)