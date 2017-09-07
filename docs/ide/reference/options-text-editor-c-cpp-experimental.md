---
title: "Opções, Editor de Texto, C/C++, Experimental | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 1677db7d5af93db8a378d598332e6a6d52f09bdd
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="options-text-editor-cc-experimental"></a>Opções, Editor de Texto, C/C++, Experimental
Ao alterar essas opções, você pode alterar o comportamento relacionado ao IntelliSense e ao banco de dados de navegação quando estiver programando em C ou C++. Esses recursos são realmente experimentais e podem ser modificados ou removidos do Visual Studio em uma versão futura. Este tópico descreve as opções no Visual Studio 2017. Para Visual Studio 2015, consulte [Opções, Editor de texto, C/C++, Experimental](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 Para acessar esta página de propriedades, pressione **Control + Q** para ativar `Quick Launch` e, em seguida, digite "experimental". O Início Rápido encontrará a página após as primeiras letras. Você também pode ir para ela, escolhendo **Ferramentas | Opções** e **Editor de Texto**, em seguida, **C/C++**e, então, escolhendo **Experimental**.  

 Esses recursos estão disponíveis em uma instalação do Visual Studio 2017.  
  
> [!NOTE]
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="enable-predictive-intellisense"></a>Habilitar IntelliSense Preditivo
O IntelliSense Preditivo limita o número de resultados exibidos na lista suspensa do IntelliSense para que você veja apenas os resultados relevantes no contexto. Por exemplo, se você digitar <code>int x =</code> e invocar a lista suspensa do IntelliSense, verá apenas inteiros ou funções que retornam inteiros. O IntelliSense Preditivo está desativado por padrão.

## <a name="enable-faster-project-load"></a>Habilitar Carregamento de Projeto Mais Rápido 
**Visual Studio 2017 versão 15.3 e posterior**: esse recurso é chamado agora de **Habilitar Cache de Projeto** e foi movido para a página de propriedades de [Configurações de Projeto do VC++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Essa opção permite que o Visual Studio coloque em cache os dados de projeto, para quando você abrir o projeto na próxima vez, ele pode carregar esses dados armazenados em cache em vez de recalcular dos arquivos de projeto. Usar dados armazenados em cache pode acelerar significativamente o tempo de carregamento do projeto.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Recursos adicionais na Galeria do Visual Studio
Para obter outros recursos do editor de texto na Galeria do Visual Studio, consulte a lista [aqui](http://go.microsoft.com/fwlink/?LinkId=692016). Um exemplo é [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f) (Correções Rápidas C++), que dá suporte ao seguinte:  
  
-   **Add missing #include (Adicionar #include ausente)** –sugere #include relevantes para símbolos desconhecidos no seu código  
  
-   **Add using namespace/Fully qualify symbol (Adicionar usando namespace/símbolo totalmente qualificado)** – semelhante ao item anterior, mas para namespaces  
  
-   **Add missing semicolon (adicionar ponto e vírgula ausente)**  
  
-   **Ajuda do MSDN** – pesquisa as mensagens de erro no MSDN  
  
 Você pode passar o mouse sobre um rabisco para obter uma lâmpada ou usar o atalho de teclado padrão Ctrl+Ponto (Ctrl+.). Observe que para o atalho de teclado, o cursor do sistema não precisa ser posicionado sobre o erro específico ou o token, você pode simplesmente estar na mesma linha do erro para invocar sugestões para qualquer item nessa linha.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando opções do editor específicas a um idioma](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refatoração em C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)

