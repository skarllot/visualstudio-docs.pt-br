---
title: "Criar configurações do editor portátil e personalizado com o EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
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
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.contentlocale: pt-br
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Criar configurações do editor portátil e personalizado com o EditorConfig
As configurações do editor de texto no Visual Studio são aplicáveis a todos os projetos de um tipo determinado. Dessa forma, por exemplo, se você alterar uma configuração do editor de texto do C#, essa configuração se aplicará a *todos* os projetos do C# no Visual Studio. No entanto, em alguns casos, convém usar convenções que diferem das suas próprias preferências pessoais do editor. Os arquivos [EditorConfig](http://editorconfig.org/) permitem fazer isso fornecendo texto opções comuns do editor de texto por projeto. As configurações do EditorConfig, contidas em um arquivo .editorconfig adicionado à sua base de código, substituem as configurações globais do editor de texto do Visual Studio. Isso significa que você poderá personalizar cada base de código para usar as configurações de editor de texto que você preferir. Não é necessário nenhum plug-in para usar essa funcionalidade no Visual Studio.

## <a name="coding-consistency"></a>Consistência de codificação
As configurações em arquivos EditorConfig permitem manter configurações e estilos de codificação consistentes para uma linguagem, como estilo de recuo, largura de tabulação, caracteres de fim de linha, codificação e mais, em uma base de código independentemente do editor ou IDE usado. Por exemplo, ao codificar em C#, se sua base de código tem uma convenção de preferir que os recuos sempre sejam compostos por cinco caracteres de espaço, que os documentos usem codificação UTF-8 e que cada linha sempre termine com uma CR/LF, é possível configurar um arquivo .editorconfig para fazer isso.

As convenções de codificação usadas em seus projetos pessoais podem ser diferentes das usadas nos projetos da sua equipe. Por exemplo, talvez você prefira apertar a tecla Tab para adicionar um caractere de tabulação enquanto você estiver codificando. No entanto, sua equipe pode preferir que o recuo adicione quatro caracteres de espaço em vez de um caractere de tabulação. Os arquivos EditorConfig resolvem esse problema permitindo que você tenha uma configuração para cada cenário.

Como as configurações estão contidas em um arquivo na base de código, elas viajam juntamente com essa base de código. Contanto que você abra o arquivo de código em um editor em conformidade com o EditorConfig, as configurações do editor de texto são implementadas. Para obter mais informações sobre arquivos EditorConfig, consulte o site [EditorConfig.org](http://editorconfig.org/). Se você editar muitos arquivos .editorconfig, talvez você ache a extensão [Serviço de linguagem do EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) útil.

## <a name="override-editorconfig-settings"></a>Substituir as configurações do EditorConfig
Quando você adiciona um arquivo .editorconfig a uma pasta em sua hierarquia de arquivos, as configurações se aplicam a todos os arquivos aplicáveis no nível e abaixo. Para substituir as configurações do EditorConfig para um projeto ou base de código específico e para usar valores de substituição ou diferentes do arquivo .editorconfig de nível superior, adicione um arquivo .editorconfig ao nível que você deseja alterar.

![Hierarquia do EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

As novas configurações do arquivo .editorconfig são aplicáveis ao nível no qual ele e seus subarquivos estão localizados.

## <a name="supported-settings"></a>Configurações com suporte
O editor do Visual Studio dá suporte aos seguintes valores do conjunto principal de opções EditorConfig.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- raiz
- [convenções de estilo de código](../ide/editorconfig-code-style-settings-reference.md)

Há suporte para as configurações do EditorConfig em todas as linguagens às que o Visual Studio dá suporte, exceto para XML.

## <a name="example"></a>Exemplo
Aqui está um exemplo que mostra o estado de recuo de um trecho de código C# antes e depois de adicionar um arquivo .editorconfig ao projeto. A configuração **Tabulações** na caixa de diálogo **Opções** do editor de texto do Visual Studio foi definida para produzir caracteres de espaço, quando você pressiona a tecla TAB no seu código.

![Configuração de tabulação do Editor de texto](../ide/media/vside_editorconfig_tabsetting.png)

Conforme esperado, pressionar a tecla TAB na próxima linha faz a linha recuar por meio da adição de quatro caracteres de espaço em branco.

![Codificar antes de usar o EditorConfig](../ide/media/vside_editorconfig_before.png)

Adicionaremos o seguinte a um novo arquivo chamado .editorconfig ao projeto. (O configuração `[*.cs]` significa que essa alteração será aplicada somente a arquivos .cs neste projeto.)

![Arquivo .editorconfig adicionado ao projeto](../ide/media/vside_editorconfig_addconfig.png)

Agora, quando você pressiona a tecla TAB, você obtém caracteres de tabulação em vez de espaços.

![TAB adiciona um caractere de tabulação](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Adicionar um arquivo .editorconfig ao seu projeto ou base de código não converterá os estilos existentes em novos; isso se aplicará somente a linhas recém-adicionadas. Se você remover um arquivo .editorconfig do seu projeto ou de sua base de código, será necessário recarregar os arquivos de código para que as configurações do editor sejam revertidas para configurações globais. Os erros em arquivos .editorconfig são informados na janela Erro no Visual Studio.

## <a name="support-editorconfig-for-your-language-service"></a>Dar suporte ao EditorConfig para o serviço de linguagem

Na maioria dos casos, ao implementar um serviço de linguagem do Visual Studio, nenhum trabalho adicional é necessário para dar suporte às propriedades universais do EditorConfig. O editor básico detecta automaticamente e lê o arquivo .editorconfig quando os usuários abrem arquivos e define as opções de buffer e exibição de texto apropriadas. No entanto, alguns serviços de linguagem optam por usar uma opção de exibição de texto contextual apropriada, em vez de usar configurações globais para itens como tabulações e espaços quando um usuário edita ou formata um texto. Nesses casos, o serviço de linguagem deve ser atualizado para dar suporte aos arquivos do EditorConfig.

A tabela a seguir lista as alterações necessárias para atualizar um serviço de linguagem para dar suporte aos arquivos do EditorConfig.

| Opção global preterida específico a um idioma | Substituição de opção contextual |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) ou !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) ou textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) ou textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>Consulte também
[Criar opções do editor portátil e personalizado com o EditorConfig](create-portable-custom-editor-options.md)
