---
title: "Como personalizar como o Visual Studio cria legendas para controles associados a dados | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "legendas, associado a dados"
  - "Janela Fontes de Dados, legendas de rótulos"
  - "Legendas de rótulos, janela Fontes de Dados"
  - "legendas inteligentes"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como personalizar como o Visual Studio cria legendas para controles associados a dados
Uma consideração especial entra em jogo quando você arrasta itens do [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para o Designer de formulários do Windows: os nomes de coluna nos rótulos de legenda são reformatados para uma cadeia de caracteres mais legível quando duas ou mais palavras são encontradas concatenadas juntas. Você pode personalizar a maneira na qual esses rótulos são criados definindo o **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** valores a **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Data Designers** chave do registro.  
  
> [!NOTE]
>  Essa chave do registro não existe até que você criá\-lo.  
  
 Títulos inteligentes são controlados pela expressão regular inserida no valor da **SmartCaptionExpression** valor. Adicionando o **Data Designers** chave do Registro substitui a expressão regular padrão que controla rótulos de legenda. Para obter mais informações sobre expressões regulares, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 A tabela a seguir descreve os valores do registro que controlam os rótulos de legenda.  
  
|Item do registro|Descrição|  
|----------------------|---------------|  
|SmartCaptionExpression|A expressão regular usada para corresponder seus padrões.|  
|SmartCaptionReplacement|O formato para exibir quaisquer grupos correspondidos no **SmartCaptionExpression**.|  
|SmartCaptionSuffix|Uma cadeia de caracteres opcional para acrescentar ao final da legenda.|  
  
 As tabelas a seguir lista as configurações padrão interno para esses valores do registro.  
  
|Item|Valor padrão|Explicação|  
|----------|------------------|----------------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\) \(\\\\p{Lu}\)&#124;\_\+|Corresponde a um caractere minúsculo seguido por um caractere maiúsculo ou um sublinhado.|  
|**SmartCaptionReplacement**|$1 $2|$1 representa quaisquer caracteres correspondidas no primeiro parênteses da expressão, e $2 representa quaisquer caracteres correspondidas no segundo parênteses. A substituição é a primeira correspondência, um espaço e, em seguida, a segunda correspondência.|  
|**SmartCaptionSuffix**|:|Representa um caractere acrescentado à cadeia de caracteres retornada. Por exemplo, se a legenda for `Company Name`, o sufixo a tornará `Company Name:`|  
  
> [!CAUTION]
>  Você deve ter muito cuidado ao fazer qualquer coisa no Editor do registro. Faça backup do registro antes de editá\-lo. Se você usar o Editor do Registro incorretamente, você pode causar sérios problemas que talvez exijam a reinstalação do sistema operacional. A Microsoft não garante que problemas causados por você usando o Editor do Registro incorretamente podem ser resolvidos. Use o Editor do registro por seu próprio risco.  
>   
>  O seguinte artigo da Base de conhecimento contém instruções para fazer backup, editar e restaurar o registro: [Descrição do registro do Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### Para modificar o comportamento inteligente legenda da janela fontes de dados  
  
1.  Abra uma janela de comando, clicando em **Iniciar** e **executar**.  
  
2.  Tipo `regedit` no **executar** caixa de diálogo e clique em **OK**.  
  
3.  Expanda o **HKEY\_CURRENT\_USER** nó.  
  
4.  Expanda o **Software** nó.  
  
5.  Expanda o **Microsoft** nó.  
  
6.  Expanda o **VisualStudio** nó.  
  
7.  Clique com botão direito do **10.0** nó e crie um novo **chave** chamado `Data Designers`.  
  
8.  Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionExpression`.  
  
9. Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionReplacement`.  
  
10. Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionSuffix`.  
  
11. Clique com botão direito do **SmartCaptionExpression** item e escolha **modificar**.  
  
12. Insira a expressão regular você deseja o **fontes de dados** janela para usar.  
  
13. Clique com botão direito do **SmartCaptionReplacement** item e escolha **modificar**.  
  
14. Insira a substituição de cadeia de caracteres formatada da maneira desejada para exibir os padrões de correspondência em sua expressão regular.  
  
15. Clique com botão direito do **SmartCaptionSuffix** item e escolha **modificar**.  
  
16. Digite quaisquer caracteres que você deseja que apareça no final da legenda.  
  
     Na próxima vez que você arrastar itens do **fontes de dados** janela, os rótulos de legenda são criados usando os novos valores de registro fornecidos.  
  
### Para desativar o recurso Títulos inteligentes  
  
1.  Abra uma janela de comando, clicando em **Iniciar** e **executar**.  
  
2.  Tipo `regedit` no **executar** caixa de diálogo e clique em **OK**.  
  
3.  Expanda o **HKEY\_CURRENT\_USER** nó.  
  
4.  Expanda o **Software** nó.  
  
5.  Expanda o **Microsoft** nó.  
  
6.  Expanda o **VisualStudio** nó.  
  
7.  Clique com botão direito do **10.0** nó e crie um novo **chave** chamado `Data Designers`.  
  
8.  Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionExpression`.  
  
9. Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionReplacement`.  
  
10. Clique com botão direito do **Designers de dados** nó e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionSuffix`.  
  
11. Clique com botão direito do **SmartCaptionExpression** item e escolha **modificar**.  
  
12. Digite `(.*)` para o valor. Isso corresponderá a seqüência inteira.  
  
13. Clique com botão direito do **SmartCaptionReplacement** item e escolha **modificar**.  
  
14. Digite `$1` para o valor. Isso substitui a cadeia de caracteres com o valor correspondente, que é a cadeia de caracteres inteira, de modo que ela permanecerá inalterada.  
  
     Na próxima vez que você arrastar itens do **fontes de dados** janela, os rótulos de legenda são criados com legendas não modificadas.  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)