---
title: "System.Activities Tab, Choose Toolbox Items Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# System.Activities Tab, Choose Toolbox Items Dialog Box
Este guia da caixa de diálogo **Escolher Itens de Caixa de Ferramentas** exibe uma lista de atividades, modelos e itens de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] disponíveis para você.  Para exibir esses lista, **Escolher Itens de Caixa de Ferramentas** partir do menu de **Ferramentas** ou clique com o botão direito do mouse **Caixa de Ferramentas** e selecionando **Escolher Itens** para exibir a caixa de diálogo **Escolher Itens de Caixa de Ferramentas** , e então selecione o guia de **System.Activities** .  Fora da caixa, a lista contém atividades de fluxo de trabalho de conjuntos de System.Activities, de System.ServiceModel.Activities, e de System.Activities.Core.Presentation; no entanto, somente o sistema forneceu as atividades mostradas e as atividades adicionados por meio de outros assemblies exibidos em **Caixa de Ferramentas** são verificadas por padrão.  As atividades recentemente adicionados automaticamente são verificadas e aparecem em **Caixa de Ferramentas** quando você clica em **OK** na caixa de diálogo.  Além disso, esses itens aparecem em **Caixa de Ferramentas** em uma nova categoria que corresponde ao namespace onde a atividade\/item\/modelo residem.  
  
> [!WARNING]
>  Se você tentar adicionar um conjunto que não contém quaisquer atividades de fluxo de trabalho, uma caixa de diálogo de erro é exibida para explicar que o assembly não contém quaisquer atividades.  
  
 Esta caixa de diálogo é projeto desconhecido e portanto o guia de **System.Activities** continua a aparecer em XAML autônomo ou em um tipo de projeto não fluxo de trabalho.  
  
 A filtragem é feita em cada guia.  Isso significa que não é possível adicionar atividades de fluxo de trabalho através da guia de **componente .NET.** Têm que ser adicionados pelo próprio guia de **System.Activities** .  
  
 Você pode limpar todos os itens que você não desejar consultar em **Caixa de Ferramentas** deste guia da caixa de diálogo, ou como alternativa, você pode fazer isso usando a opção de menu de contexto **Excluir** em **Caixa de Ferramentas** e de\- fazendo referência a um assembly não remove o item de **Caixa de Ferramentas**.  
  
 Criando uma instância da atividade, arrastando e soltando\-os ao designer adiciona o assembly que contém o item à lista de módulos \(assemblies\) referenciados automaticamente.  Também se a atividade referencia um assembly C 2.0, C 2.0 não adiciona à lista de assembly referenciado.  O assembly C 2.0 tem que estar no GAC ou no mesmo diretório que a atividade B.  Em casos autônomos, o assembly não tem que estar em GAC ou nos caminhos de investigação de CONTRA.  Somente então você pode arrastar e soltar a atividade na superfície de fluxo de trabalho.  
  
 as configurações de**Caixa de Ferramentas** são salvos por padrão como opções de usuário, então a próxima vez, quando você abre **Caixa de Ferramentas**, ele exibe sua lista personalizado de atividades de fluxo de trabalho.  Um efeito colateral disso é que se você adicionou seus itens específicos de domínio para **Caixa de Ferramentas** através da caixa de diálogo **Escolher Itens de Caixa de Ferramentas** , você ainda continuará a consulte esses itens quando você estiver trabalhando em um aplicativo de console do fluxo de trabalho também.  Se você não deseja os consulte, então excluir\-los que usam o menu de contexto ou desmarcar\-los através da caixa de diálogo **Escolher Itens de Caixa de Ferramentas** como observados anteriormente.  
  
 As colunas nesta caixa de diálogo contém as informações a seguir:  
  
 Nome  
 Lista os nomes das atividades de fluxo de trabalho registradas atualmente em seu computador local.  
  
 Namespace  
 Exibe a hierarquia de namespace de biblioteca de classes do.NET Framework que define a estrutura de atividade.  
  
 Nome do Assembly  
 Exibe o nome e a versão do assembly do.NET Framework que contém a atividade.  
  
 Diretório  
 Exibe o local do assembly do.NET Framework que contém as atividades de fluxo de trabalho.  O local padrão para todos os assemblies é o cachê global de assemblies.  
  
 Para classificar os componentes listados, selecione todo o título de coluna.