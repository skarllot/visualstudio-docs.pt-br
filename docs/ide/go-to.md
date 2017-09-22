---
title: Ir para | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: gewarren
ms.author: gewarren
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
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.contentlocale: pt-br
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>Ir para
Há várias maneiras de navegar facilmente pelo código dentro do IDE do Visual Studio, tanto pelo teclado quanto pelo mouse.

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>Ir para Todos
Esse recurso existe no Visual Studio 2017 e posterior.  Ele permite navegar pelo código para localizar as partes específicas que você está procurando.  É possível pesquisar uma linha, um tipo, um símbolo, um arquivo específico e muito mais em uma interface simples e unificada.

### <a name="how-to-use"></a>Como usar
* **Teclado**
  * Pressione **Ctrl+** ou **Ctrl+T**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
* **Mouse**
  * Selecione **Editar > Ir Para > Ir para Todos**.

Isso exibirá uma pequena janela na parte superior direita do IDE, por padrão.

![Ir para Todos](media/gotoall.png)

Aqui, há várias maneiras de continuar:
* Insira o texto sem um prefixo para pesquisar usando os [ícones de filtro](#filtered-searches) selecionados abaixo da caixa de texto.
* Insira um [prefixo](#filtered-searches) seguido pelo texto a ser pesquisado.
* Insira um ponto de interrogação (?) para obter ajuda adicional.
  ![Ajuda de Ir para Todos](media/gotoall_help.png)

### <a name="filtered-searches"></a>Pesquisas filtradas
Para restringir sua pesquisa a um tipo específico, você pode usar um prefixo ao digitar ou usar os ícones abaixo da janela de pesquisa, como mostrado abaixo.

Prefixo | Ícone | Atalho | Descrição
:----: | ---- | -------- | ---
#      | ![Ícone do símbolo](media/gotoall_symbolicon.png) | Ctrl+1, Ctrl+S | Localizar símbolos correspondentes
f      | ![Ícone de Arquivo](media/gotoall_fileicon.png)     | Ctrl+1, Ctrl+F | Localizar nomes de arquivo correspondentes
m      | ![Ícone do Membro](media/gotoall_membericon.png) | Ctrl+1, Ctrl+M | Localizar membros correspondentes
t      | ![Ícone de Tipo](media/gotoall_typeicon.png)     | Ctrl+1, Ctrl+T | Localizar tipos correspondentes
:      | ![Ícone de Linha](media/gotoall_lineicon.png)     | Ctrl+G         | Ir para o número de linha inserido

### <a name="search-locations"></a>Locais de pesquisa
Para restringir sua pesquisa para locais específicos, use os dois ícones de documento.

Ícone | Descrição
---- | ---
![Documento Atual](media/gotoall_currentdocument.png) | Pesquisar apenas o documento atual
![Documentos Externos](media/gotoall_external.png) | Pesquisar documentos externos além daqueles localizados no projeto/solução

### <a name="settings"></a>Configurações
Clicar no ícone de engrenagem ![Ícone de engrenagem](media/gotoall_gear.png) no canto inferior direito permite alterar como esse recurso funciona.

Configuração | Descrição
------- | ---
Usar guia de visualização | Exibir o item selecionado imediatamente na guia de visualização do IDE
Mostrar detalhes    | Exibir informações do projeto, arquivo, linha e resumo dos comentários de documentação na janela
Centralizar janela   | Mover esta janela para o centro do IDE em vez de para a parte superior direita
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>Ir para definição
Navegue até a fonte de um tipo e abra o resultado em uma nova guia:

Entrada        | Função 
------------ | ---
**Teclado** | Coloque o cursor de texto em algum lugar dentro do nome do tipo e pressione **F12**
**Mouse**    | Clique com o botão direito do mouse no nome do tipo e selecione **Ir para Definição**

## <a name="peek-definition"></a>Inspecionar Definição
Visualize a definição de um tipo em uma janela pop-up em vez de em uma nova guia:

Entrada        | Função 
------------ | ---
**Teclado** | Coloque o cursor de texto em algum lugar dentro do nome do tipo e pressione **Alt+F12**
**Mouse**    | Clique com o botão direito do mouse no nome do tipo e selecione **Inspecionar Definição**

Se você inspecionar outra definição da janela pop-up, iniciará um caminho de navegação estrutural no qual poderá navegar usando os círculos e setas que aparecem acima da janela pop-up.  Para obter mais informações, consulte [How to: View and Edit Code by Using Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Como exibir e editar códigos usando Inspecionar Definição (Alt + F12)).

## <a name="go-to-implementation"></a>Ir Para Implementação
Navegue de uma classe base ou tipo para suas implementações.  Se houver várias implementações, você as verá listadas na janela **Localizar Resultados de Símbolos**:

Entrada        | Função 
------------ | ---
**Teclado** | Coloque o cursor de texto em algum lugar dentro do nome do tipo e pressione **Ctrl+F12**
**Mouse**    | Clique com o botão direito do mouse no nome do tipo e selecione **Ir Para Implementação**

## <a name="find-all-references"></a>Localizar Todas as Referências
Localize todos os locais em que um método/propriedade/variável está sendo usada.  Você pode usar isso para verificar o código morto e verificar possíveis efeitos colaterais de uma grande refatoração.  Pressione **F8** para pular entre os resultados.

Entrada        | Função 
------------ | ---
**Teclado** | Coloque o cursor de texto em algum lugar dentro do nome do tipo e pressione **Ctrl+K, R**
**Mouse**    | Clique com o botão direito do mouse no nome do tipo e selecione **Localizar Todas as Referências**

## <a name="navigating-results"></a>Navegando nos resultados
Ao usar os recursos de navegação do Visual Studio, você pode navegar para frente e para trás pela pilha:

Entrada        | Função 
------------ | ---
**Ctrl+-**          | Navegue para trás pela pilha
**Ctrl+Shift+-**    | Navegue para frente pela pilha

Você também pode usar os itens de menu **Exibir > Navegar para Trás** e **Exibir > Navegar para Frente**.
