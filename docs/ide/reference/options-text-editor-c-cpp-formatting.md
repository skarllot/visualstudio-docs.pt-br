---
title: "Opções, Editor de Texto, C-C++, Formatação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0fc25d6ed45929764b5d8cb64df935dd14886f1e
ms.lasthandoff: 02/22/2017

---
# <a name="options-text-editor-cc-formatting"></a>Opções, Editor de Texto, C/C++, Formatação
Permite alterar o comportamento padrão do Editor de Códigos quando você está programando no C ou C++.  
  
 Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e clique em **Formatação**.  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="cc-options"></a>Opções do C/C++  
 **Habilitar a dica de ferramenta automática Informações Rápidas**  
 Habilita ou desabilita o recurso IntelliSense de Informações Rápidas.  
  
## <a name="inactive-code"></a>Código inativo  
 **Mostrar blocos de códigos inativos**  
 O código que está inativo devido às declarações `#ifdef` é colorido de forma diferente para ajudar você a identificá-lo.  
  
 **Desabilitar a opacidade de código inativo**  
 O código inativo pode ser identificado usando cor em vez de transparência.  
  
 **Percentual de opacidade de código inativo**  
 O grau de opacidade para blocos de códigos inativos pode ser personalizado.  
  
## <a name="indentation"></a>Recuo  
 **Recuar chaves**  
 Você pode configurar como as chaves são alinhadas quando pressiona ENTER depois de iniciar um bloco de códigos, por exemplo, uma função ou um loop `for`. As chaves podem ser alinhadas com o primeiro caractere do bloco de códigos ou recuadas.  
  
 **Recuo automático na tabulação**  
 Você pode configurar o que acontece na linha de código atual quando você pressiona TAB. A linha é recuada ou uma tabulação é inserida.  
  
## <a name="miscellaneous"></a>Diversos  
 **Enumerar os comentários na janela Lista de Tarefas**  
 O editor pode verificar arquivos de software livre em busca de palavras predefinidas nos comentários. Ele cria uma entrada na janela **Lista de Tarefas** para qualquer palavra-chave encontrada.  
  
 **Realçar tokens correspondentes**  
 Quando o cursor está próximo a uma chave, o editor pode realçar a chave correspondente para que você possa ver mais facilmente o código contido.  
  
## <a name="outlining"></a>Estrutura de tópicos  
 **Entrar no modo de estrutura de tópicos na abertura dos arquivos**  
 Quando você insere um arquivo no editor de texto, é possível habilitar o recurso de estrutura de tópicos. Para obter mais informações, consulte [Estrutura de tópicos](../../ide/outlining.md). Quando essa opção é selecionada, o recurso de estrutura de tópicos é habilitado quando você abre um arquivo.  
  
 **Estrutura de tópicos automática de blocos de região #pragma**  
 Quando essa opção é selecionada, a estrutura de tópicos automática de [diretivas pragma](/visual-cpp/preprocessor/pragma-directives-and-the-pragma-keyword) é habilitada. Isso permite expandir ou recolher blocos de região pragma no modo de estrutura de tópicos.  
  
 **Estrutura de tópicos automática de blocos de instrução**  
 Quando essa opção é selecionada, a estrutura de tópicos automática é habilitada para os seguintes construtores de instrução:  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [Instrução switch (C++)](/visual-cpp/cpp/switch-statement-cpp)  
  
-   [Instrução while (C++)](/visual-cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)   
 [Usando o IntelliSense](../../ide/using-intellisense.md)
