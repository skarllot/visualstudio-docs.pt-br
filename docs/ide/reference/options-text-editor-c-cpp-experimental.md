---
title: "Opções, Editor de Texto, C/C++, Experimental | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: a1edc88394193474b273968d8435e8df06415044
ms.openlocfilehash: a3fcafe5c191987668dc6e0dce8835d748742ed7

---
# <a name="options-text-editor-cc-experimental"></a>Opções, Editor de Texto, C/C++, Experimental
Ao alterar essas opções, você pode alterar o comportamento relacionado ao IntelliSense e ao banco de dados de navegação quando estiver programando em C ou C++.  
  
 Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e escolha **Experimental**.  
  
 Esses recursos estão disponíveis em uma instalação do Visual Studio 2015 Atualização 1 RC.  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Navegação  
 **Habilitar Novo Mecanismo de Banco de Dados**  
 Isso deve automaticamente acelerar a população de banco de dados e tornar todas as operações de banco de dados mais rápidas (sem nenhuma perda de precisão) para operações como **Ir para Definição** e **Localizar Todas as Referências**. (Apenas feche e reabra a solução para aplicar as alterações, você não precisa reiniciar o Visual Studio.)  
  
## <a name="intellisense"></a>IntelliSense  
 **Lista de Membros Ponto-a-Seta**  
 Substitui '.' por '->' quando aplicável para a lista de membros.  
  
## <a name="refactoring"></a>Refatoração  
 **Habilitar Extrair Função**  
 Extrai o código selecionado para sua própria função e substitui o código com uma chamada para a nova função. Para acessar esse recurso, clique com botão direito do mouse no código selecionado e selecione **Ações Rápidas** ou simplesmente pressione o atalho padrão Ctrl+Ponto [Ctrl+.].  
  
 **Habilitar Alteração de Assinatura**  
 Adiciona, reordena e exclui parâmetros de uma função e propaga as alterações para todos os sites de chamada. Para acessar esse recurso, clique com botão direito do mouse em qualquer uso da função e selecione **Ações Rápidas** ou simplesmente pressione o atalho padrão Ctrl+Ponto [Ctrl+.].  
  
## <a name="text-editor"></a>Editor de Texto  
 **Habilitar Expandir Escopos**  
 Se habilitado, você poderá colocar o texto selecionado entre chaves digitando ‘{’ no editor de texto.  
  
 **Habilitar Expandir Precedência**  
 Se habilitado, você poderá colocar o texto selecionado entre parênteses digitando ‘(’ no editor de texto.  
  
 Para recursos adicionais do editor de texto na Galeria do Visual Studio, consulte a lista [aqui](http://go.microsoft.com/fwlink/?LinkId=692016). Um exemplo é [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f) (Correções Rápidas C++), que dá suporte ao seguinte:  
  
-   **Add missing #include (Adicionar #include ausente)** –sugere #include relevantes para símbolos desconhecidos no seu código  
  
-   **Add using namespace/Fully qualify symbol (Adicionar usando namespace/símbolo totalmente qualificado)** – semelhante ao item anterior, mas para namespaces  
  
-   **Add missing semicolon (adicionar ponto e vírgula ausente)**  
  
-   **Ajuda do MSDN** – pesquisa as mensagens de erro no MSDN  
  
 Você pode passar o mouse sobre um rabisco para obter uma lâmpada ou usar o atalho de teclado padrão Ctrl+Ponto (Ctrl+.). Observe que para o atalho de teclado, o cursor do sistema não precisa ser posicionado sobre o erro específico ou o token, você pode simplesmente estar na mesma linha do erro para invocar sugestões para qualquer item nessa linha.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando opções do editor específicas a um idioma](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refatoração em C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)



<!--HONumber=Feb17_HO4-->


