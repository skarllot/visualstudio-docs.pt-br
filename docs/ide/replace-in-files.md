---
title: Localizar em Arquivos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 79206d09446dcd76654c3c24976fab3fe65e4f83
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# Substituir nos Arquivos
<a id="replace-in-files" class="xliff"></a>
**Substituir nos Arquivos** permite pesquisar o código de um conjunto especificado de arquivos para uma cadeia de caracteres ou expressão e alterar algumas ou todas as correspondências encontradas. As correspondências encontradas e as ações executadas são listadas na janela **Localizar Resultados** selecionada em **Opções de resultado**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 É possível usar qualquer um dos métodos a seguir para exibir **Substituir nos Arquivos** na janela **Localizar e Substituir**.  
  
### Para exibir Substituir nos Arquivos
<a id="to-display-replace-in-files" class="xliff"></a>  
  
1.  No menu **Editar**, expanda **Localizar e Substituir**.  
  
2.  Escolha **Substituir nos Arquivos**.  
  
     – ou —  
  
     Se a janela **Localizar e Substituir** ainda estiver aberta, na barra de ferramentas, escolha **Substituir nos Arquivos**.  
  
## Localizar
<a id="find-what" class="xliff"></a>  
 Para pesquisar uma nova cadeia de caracteres de texto ou expressão, especifique-a na caixa. Para pesquisar qualquer uma das 20 cadeias de caracteres mais pesquisadas recentemente, abra a lista e escolha a cadeia de caracteres que você deseja pesquisar. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de pesquisa. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Substituir por
<a id="replace-with" class="xliff"></a>  
 Para substituir instâncias da cadeia de caracteres na caixa **Localizar** por outra cadeia de caracteres, digite a cadeia de caracteres de substituição na caixa **Substituir por**. Para excluir instâncias da cadeia de caracteres na caixa **O que localizar**, deixe esse campo em branco. Abra a lista para exibir as 20 cadeias de caracteres que você pesquisou mais recentemente. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de substituição. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Examinar
<a id="look-in" class="xliff"></a>  
 A opção escolhida na lista suspensa **Examinar** determina se **Substituir nos Arquivos** pesquisa apenas em arquivos ativos ou em todos os arquivos armazenados em determinadas pastas. Selecione um escopo da pesquisa na lista, digite um caminho de pasta ou clique no botão **Procurar (...)**  para exibir a caixa de diálogo **Escolher Pastas de Pesquisa** e escolha um conjunto de pastas a pesquisar. Também é possível digitar um caminho diretamente na caixa **Examinar**.  
  
> [!NOTE]
>  Se a opção **Examinar** selecionada fizer com que você pesquise um arquivo do qual você fez check-out do controle do código-fonte, apenas a versão desse arquivo que tiver sido baixada em seu computador local será pesquisada.  
  
## Opções de busca
<a id="find-options" class="xliff"></a>  
 É possível expandir ou recolher a seção **Localizar opções**. As opções a seguir podem ser marcadas ou desmarcadas:  
  
 Diferenciar maiúsculas de minúsculas  
 Quando selecionada, as janelas **Localizar Resultados** só exibem instâncias da cadeia de caracteres **Localizar** que coincidam tanto em termos de conteúdo quanto de maiúsculas e minúsculas. Por exemplo, uma pesquisa por "MyObject" com **Coincidir com maiúsculas e minúsculas** selecionado retornará "MyObject", mas não "myobject" nem "MYOBJECT".  
  
 Coincidir palavra inteira  
 Quando selecionada, as janelas **Localizar Resultados** só exibirão instâncias da cadeia de caracteres **O que localizar** que coincidam em palavras inteiras. Por exemplo, uma pesquisa por "MyObject" retornará "MyObject", mas não "CMyObject" nem "MyObjectC".  
  
 Usar Expressões Regulares  
 Quando essa caixa de seleção está marcada, é possível usar notações especiais para definir padrões de texto nas caixas de texto **Localizar** ou **Substituir por**. Para obter uma lista dessas notações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Procurar nestes tipos de arquivos  
 Essa lista indica os tipos de arquivos a serem pesquisados nos diretórios **Examinar**. Se esse campo for deixado em branco, todos os arquivos nos diretórios **Examinar** serão pesquisados.  
  
 Selecione qualquer item na lista para inserir uma cadeia de caracteres de pesquisa pré-configurada que localizará arquivos desses tipos específicos.  
  
## Opções de resultado
<a id="result-options" class="xliff"></a>  
 É possível expandir ou recolher a seção **Opções de resultado**. As opções a seguir podem ser marcadas ou desmarcadas:  
  
 Janela Localizar Resultados 1  
 Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 1**. Esta janela é aberta automaticamente para exibir os resultados da pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 1**.  
  
 Janela Localizar Resultados 2  
 Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 2**. Esta janela é aberta automaticamente para exibir os resultados da pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 2**.  
  
 Exibir apenas nomes de arquivos  
 Quando essa caixa de seleção estiver marcada, as janelas Localizar Resultados listarão os nomes completos e os caminhos para todos os arquivos que contêm a cadeia de caracteres de pesquisa. No entanto, os resultados não incluirão a linha de código na qual a cadeia de caracteres é exibida. Essa caixa de seleção só está disponível para Localizar em Arquivos.  
  
 Manter arquivos modificados abertos após Substituir Tudo  
 Quando selecionada, deixa abertos todos os arquivos nos quais foram feitas substituições, portanto, você pode desfazer ou salvar as alterações. Restrições de memória podem limitar o número de arquivos podem permanecer abertos após uma operação de substituição.  
  
> [!CAUTION]
>  Você pode usar **Desfazer** somente em arquivos que permanecem abertos para edição. Se essa opção não for selecionada, arquivos que não ainda estiverem abertos para edição permanecerão fechados e nenhuma opção **Desfazer** estará disponível nesses arquivos.  
  
## Consulte também
<a id="see-also" class="xliff"></a>  
 [Localizando e substituindo texto](../ide/finding-and-replacing-text.md)   
 [Localizar nos Arquivos](../ide/find-in-files.md)   
 [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md)
