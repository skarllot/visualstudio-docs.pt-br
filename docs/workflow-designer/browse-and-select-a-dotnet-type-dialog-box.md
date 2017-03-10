---
title: "Browse and Select a .NET Type Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeBrowser.UI"
  - "ActivityTypeResolver.UI"
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
caps.handback.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Browse and Select a .NET Type Dialog Box
Na janela de **Propriedades** , caixas de diálogo, ou os designers como o designer variável, quando você seleciona **Navegue para tipos…** de uma lista de tipos de dados, são a caixa de diálogo **Procurar e selecione um tipo de .NET** \(referida em um formulário como abreviado do tipo “navegador "\).  Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore de assemblies e de projetos.  
  
 Esta caixa de diálogo é empregada em um número de cenários do usuário, incluindo o seguinte:  
  
-   Ao definir o tipo de uma variável ou um argumento.  
  
-   Ao selecionar um tipo para uma atividade genérico.  
  
-   Para adicionar uma captura na atividade de <xref:System.Activities.Statements.TryCatch> .  
  
> [!NOTE]
>  O navegador do tipo pode exibir tipos de jagged array Visual Basic, mas não tipos de matriz multidimensional.  Consulte [matrizes denteadas](http://go.microsoft.com/fwlink/?LinkId=195226) e [matrizes multidimensionais](http://go.microsoft.com/fwlink/?LinkId=195227) para obter detalhes.  
  
## Selecionando um tipo de valor ou tipo de referência de navegador de tipo  
  
#### Para selecionar um valor ou uma referência digite de navegador de tipo  
  
1.  Na caixa de **Nome de Tipo** , digite o nome do tipo que você deseja usar.  
  
2.  Siga um destes procedimentos:  
  
    -   Uma vez que o nome do tipo que você deseja usar aparece na árvore na caixa de **Nome de Tipo** , clique duas vezes no tipo para selecioná\-lo.  
  
    -   O tipo suficiente caracteres na caixa de **Nome de Tipo** para identificar exclusivamente o tipo que você deseja usar e então pressione ENTER para selecionar o tipo  
  
#### Para selecionar um tipo genérico de navegador de tipo  
  
1.  Na caixa de **Nome de Tipo** , digite o nome do tipo que você deseja usar.  
  
2.  Uma vez que o nome do tipo que você deseja usar aparece na árvore na caixa de **Nome de Tipo** , clique no tipo para selecioná\-lo para causar caixas suspensas aparece.  
  
     Selecione o tipo que você deseja usar para fechar o genérico caixas suspensas, e clique em **OK**.  
  
## Tipos exibidos no navegador de tipo  
 Os tipos exibidos no navegador do tipo podem variar dependendo de como o navegador de tipo foi iniciado.  Se o navegador de tipo foi iniciado de um projeto de fluxo de trabalho dentro de **vs2010**, por padrão qualquer tipo em assemblies referenciados e referenciou projetos são mostrados.  Se o navegador de tipo foi iniciado fora de um sistema do projeto de **vs2010** \(como em um aplicativo de fluxo de trabalho rehosted ou em um arquivo autônomo de fluxo de trabalho\), então os tipos de todos os assemblies carregados em Appdomain são mostradas por padrão.  
  
 No navegador de tipo pode ser filtro por desenvolvedores do designer de atividade.  Para quaisquer atividades determinada, você pode ver apenas um subconjunto dos tipos.  Por exemplo, na atividade de <xref:System.Activities.Statements.TryCatch> , somente os tipos derivados de <xref:System.Exception> são mostrados no navegador do tipo.  
  
## Resultados de pesquisa de filtragem no navegador de tipo  
 A lista de tipos na caixa de **Nome de Tipo** obtém mais curto medida que você digita mais caracteres para encontrar uma correspondência.  Somente tipos cujo nome totalmente qualificado começa com a cadeia de caracteres que você digitou ou tipos cujo nome curto começa com a cadeia de caracteres que você digitou aparecem na lista filtrada.  
  
 Por exemplo:  
  
1.  Digitando correspondências <xref:System.OperationCanceledException> mas não <xref:System.InvalidOperationException>de **Operação** .  Para corresponder <xref:System.InvalidOperationException>, inicie digite System.I ou inválido.  
  
2.  Digitando correspondências <xref:System.GenericUriParser> de **Genérica** mas não tipos no namespace <xref:System.Collections.Generic> .  Para procurar por tipos no namespace <xref:System.Collections.Generic> , digite o nome totalmente qualificado do namespace.  
  
## Selecionando um contrato de serviço usando a caixa de diálogo de navegador de tipo  
 Ao selecionar um tipo de contrato de serviço, o navegador do tipo mostra somente os tipos que têm o atributo de <xref:System.ServiceModel.ServiceContractAttribute> .  
  
## Consulte também  
 [Using the Activity Designers](../workflow-designer/using-the-activity-designers.md)