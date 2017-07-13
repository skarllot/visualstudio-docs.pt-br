---
title: "Criando soluções e projetos | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# Criar soluções e projetos
<a id="create-solutions-and-projects" class="xliff"></a>
Os projetos são os contêineres lógicos para tudo que é necessário para criar seu aplicativo. Quando você cria um projeto escolhendo **Arquivo**, **Novo**; **Projeto** no menu principal, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria uma solução para contê-lo. Em seguida, é possível adicionar projetos novos ou existentes à solução, se necessário. É possível criar projetos de arquivos de código existentes e criar projetos temporários (apenas .NET) que serão excluídos quando você não os quiser mais.

> [!NOTE]
>  As descrições deste tópico baseiam-se na edição Visual Studio Community. As caixas de diálogo e comandos de menu que você vê podem ser diferentes dos descritos aqui, dependendo de suas configurações ou da edição Visual Studio. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## Criar um projeto com base em um modelo de projeto instalado
<a id="create-a-project-from-an-installed-project-template" class="xliff"></a>  
 Selecione **Arquivo**, **Novo**, **Projeto** no menu principal para exibir a caixa de diálogo Novo Projeto. No painel esquerdo em **Instalado**, **Modelos**, escolha a linguagem de programação e plataforma ou tecnologia, em seguida, escolha um dos modelos disponíveis no painel central.  

 Na caixa de diálogo **Novo Projeto**, o menu suspenso **Solução** oferece a opção de criar o novo projeto em uma solução nova ou existente ou em uma nova instância do Visual Studio.  

## Criar um projeto com base em arquivos de código existentes
<a id="create-a-project-from-existing-code-files" class="xliff"></a>  
 Se você tiver uma coleção de arquivos de origem flexíveis, será possível criar facilmente um projeto que os contenha. Escolha **Arquivo**, **Novo**; **Projeto de Código Existente** para iniciar o assistente de **Criação de Projetos de Arquivos de Códigos Existentes** e siga os prompts.  

> [!TIP]
>  Essa opção funciona melhor para coleções de arquivos relativamente simples.  

## Criar um projeto temporário (C# e Visual Basic)
<a id="create-a-temporary-project-c-and-visual-basic" class="xliff"></a>
 Trabalhando com projetos temporários, é possível criar e testar um projeto .NET sem especificar um local de disco. Quando você cria um projeto, basta selecionar um tipo e modelo de projeto e especificar um nome na caixa de diálogo **Novo Projeto**. A qualquer momento enquanto você está trabalhando com o projeto temporário, é possível salvá-lo ou descartá-lo.  

## Criar um projeto .NET que direciona uma versão específica do .NET Framework
<a id="create-a-net-project-that-targets-a-specific-version-of-the-net-framework" class="xliff"></a>  
 É possível criar um projeto para direcionar versões anteriores do .NET Framework usando o menu suspenso de versão do **.NET Framework** na parte superior da caixa de diálogo **Novo Projeto**. Defina esse valor antes de selecionar um modelo de projeto, uma vez que apenas modelos compatíveis com essa versão do .NET Framework serão exibidos na lista.  

 É necessário ter o .NET Framework 3.5 instalado em seu sistema para acessar as versões de estrutura anteriores à versão 4.0.  

## Baixar soluções de amostra
<a id="download-sample-solutions" class="xliff"></a>  
 É possível usar o Visual Studio para baixar e instalar soluções de amostra na [Galeria de Códigos do MSDN](http://go.microsoft.com/fwlink/?LinkId=254185), assim como em outras fontes, como repositórios Git.

 É possível baixar as amostras individualmente ou baixar um Pacote de Amostras que contém amostras relacionadas que compartilham uma tecnologia ou tópico. Você receberá uma notificação quando as alterações no código-fonte forem publicadas para qualquer exemplo baixado.  

 Para obter mais informações, consulte [Amostras do Visual Studio](../ide/visual-studio-samples.md).  

## Adicionar arquivos individuais no nível da solução
<a id="add-single-files-at-the-solution-level" class="xliff"></a>  
 Às vezes, você pode ter um arquivo que vários projetos referenciam ou que contém dados de texto ou diversos que pertencem logicamente no nível da solução em vez de em um projeto específico.  Para adicionar um item individual a uma solução:  

- Clique com o botão direito do mouse no nó da solução em **Gerenciador de Soluções** e escolha **Adicionar**, **Novo Item** ou **Adicionar**, **Item Existente**.  

## Criar soluções vazias
<a id="create-empty-solutions" class="xliff"></a>  
 Embora os projetos possam residir em uma solução, também é possível criar soluções que não tenham projetos. Você também pode abrir projetos de código sem precisar de uma solução.

#### Para criar uma solução vazia
<a id="to-create-an-empty-solution" class="xliff"></a>  

1.  No menu **Arquivo**, escolha **Novo**, **Novo Projeto**.  

2.  No painel esquerdo, escolha **Instalado**, **Outros Tipos de Projeto**, **Soluções do Visual Studio** na lista expandida.  

3.  No painel central, selecione **Solução em Branco**.  

4.  Defina os valores **Nome** e **Local** para sua solução e, em seguida, clique em **OK**.  

Depois de criar uma solução vazia, é possível adicionar projetos novos ou existentes ou itens a ele ao selecionar **Adicionar Novo Item** ou **Adicionar Item Existente** no menu **Projeto**.

### Excluir soluções
<a id="delete-solutions" class="xliff"></a>  
 É possível excluir uma solução permanentemente, mas não usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Antes de excluir uma solução, mova os projetos que você pode deseja usar novamente em outra solução. Em seguida, use o Gerenciador de Arquivos para excluir o diretório que contém os arquivos de solução .sln e .suo.  

> [!NOTE]
>  O arquivo .suo é um arquivo oculto que não é exibido nas configurações do Gerenciador de Arquivos padrão.  

##### Para excluir uma solução
<a id="to-delete-a-solution" class="xliff"></a>  

1.  Em **Gerenciador de Soluções**, no menu de contexto (clicando com o botão direito do mouse) da solução que deseja excluir, selecione **Abrir pasta no Explorador de Arquivos**.

2.  No Gerenciador de Arquivos, navegue um nível acima.

3.  Selecione o diretório que contém a solução e pressione a tecla DELETE.

## Consulte também
<a id="see-also" class="xliff"></a>  
 [Soluções e projetos](../ide/solutions-and-projects-in-visual-studio.md)   

