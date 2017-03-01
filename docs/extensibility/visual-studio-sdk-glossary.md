---
title: "Glossário do Visual Studio SDK | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4b5243ea3fd5364e2b14eb9edab7648852634728
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk-glossary"></a>Glossário do Visual Studio SDK
Este glossário fornece definições de termos que são usados no [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentação.  
  
## <a name="terms"></a>Termos  
 suplemento de com  
 Um aplicativo de utilitário, driver ou outro software adicionadas a um aplicativo principal. No ambiente de desenvolvimento integrado do Visual Studio (IDE), um suplemento é um aplicativo baseado em automação que estende os recursos do IDE.  
  
 modelo de automação  
 O modelo de automação, conhecido em versões anteriores do Visual Studio como o modelo de extensibilidade, é uma interface de programação que lhe dá acesso às rotinas subjacentes unidade IDE. Macros, suplementos e assistentes usam objetos no modelo de automação para controlar ou estendem a funcionalidade do IDE.  
  
 contexto de interface de usuário de comando  
 Associação de um GUID com a visibilidade de um elemento, como uma barra de ferramentas ou um comando de interface do usuário. Contexto de interface de usuário do comando é diferente de contexto de seleção que não está anexado a uma janela.  
  
 Contexto de interface de usuário de comando pode ser usado para:  
  
-   Atribua um GUID para uma barra de ferramentas é exibida quando uma janela específica for ativada.  
  
-   Atribua um GUID para a disponibilidade de um comando sem a necessidade de carregar ou executar um VSPackage.  
  
-   Atribua um GUID para afetar a associação de chave ativa.  
  
-   Atribua um GUID para ativar a gravação de macros.  
  
-   Atribua um GUID para ativar o modo de depuração ou para alternar entre o design e o modo de execução em um editor.  
  
 componente  
 Parte do software que pode ser feito parte da funcionalidade de um aplicativo sem esse aplicativo com todas as informações sobre a implementação do software já existentes. A comunicação entre um componente e um aplicativo é somente por meio de interfaces de estilo OLE.  
  
 Gerenciador de componentes  
 Um serviço, `SOleComponentManager`, que fornece serviços de coordenação de interface do usuário não para componentes de nível superior. O `SOleComponentManager` serviço implementa a `IOleComponentManager` interface.  
  
 Gerenciador de componentes da interface do usuário  
 Um serviço, `SOleComponentUIManager`, que fornece serviços de coordenação de interface do usuário. O `SOleComponentUIManager` serviço implementa a `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfaces.  
  
 recipiente de contexto  
 Um `IVsUserContext` COM (objeto) anexado a um componente do ambiente. Esse objeto contém atributos relacionados ao componente, palavras-chave F1 e palavras-chave de pesquisa. Além disso, recipientes de contexto ponto para qualquer recipientes subcontexto que estão vinculados a eles.  
  
 provedor de contexto  
 Um componente no IDE que tem um recipiente de contexto associado a ele. Esses componentes incluem uma janela da ferramenta, o editor ou a hierarquia de projeto.  
  
 designer  
 Uma interface de programação que permite aos usuários manipular elementos da interface do usuário (formulários, botões e outros controles).  
  
 DocData  
 Um objeto COM que encapsula os dados subjacentes de um documento em um mundo onde há separação de documento/exibição (por exemplo, no caso do editor de texto, isso seria o buffer de texto subjacente todas as exibições do editor de texto). Se o EditorFactory não fornecer esse objeto, o IDE produzirá um em seu nome. A responsabilidade desse objeto é gerenciar a persistência de dados e a semântica de compartilhamento de vários modos de exibição sobre isso mesmo `DocData`. Se o `DocData` objeto oferece suporte a `IOleCommandTarget` interface, ele será incluído no roteamento de comando da UIShell.  
  
 DocObject  
 Tecnologia usada para hospedar a interface do usuário em um intervalo fornecido pelo host. Mais especificamente, esse termo refere-se a qualquer incorporação que ofereça suporte a `IOleDocument` e das interfaces relacionadas. Essa tecnologia tem muitos aplicativos potenciais como um detalhe de implementação de documentos COM, janelas de ferramenta no Visual Basic 5.0, designers do ActiveX no Visual Basic 6.0 e assim por diante.  
  
 documento  
 Usado para se referir genericamente ao documento como um todo — tanto o `DocData` e `DocView`. Por exemplo, um DocumentFrame contém uma `DocView`, mas também mantém uma referência para o `DocData` para lidar com persistência.  
  
 DocView  
 O DocObject/incorporando/WindowPane com a qual o usuário interage para exibir e manipular subjacente `DocData`. Observe que os usuários não tirar proveito da separação de documento/exibição que é parte do `DocObject` design de interface. Os usuários usam um DocObject todo para atuar como um modo de exibição em vez de usar um conceito mais abstrato (e menos formalizado) dos dados subjacentes, conhecidos como `DocData`. `DocView`objetos sempre são inseridos com objetos de quadro do documento (janelas MDI filhas) do IDE.  
  
 DTE  
 O `DTE` objeto (extensibilidade de ferramentas de desenvolvimento) é o ponto de acesso mais alto no modelo de automação do Visual Studio, que permite automatizar e estender o IDE de forma programática.  
  
 Janela de ajuda dinâmica  
 Janela de ferramenta que é implementada pelo IDE e exibe uma lista de tópicos da Ajuda F1 ou de palavra-chave de pesquisa.  
  
 editor  
 Código (CLSID classe) que implementa o `DocView`. Ele também implementa `DocData` se há suporte para a separação de dados/exibição.  
  
 extensão  
 Um recurso que modifica, personaliza ou adiciona um IDE. Crie extensões usando o modelo de automação ou VSPackages.  
  
 editor externo  
 Um editor que não é específico para o IDE, como o Microsoft Word. Ele foi registrado por meio de seus próprios mecanismos e pode ser usado fora do IDE. Se este editor pode ser inserido, ele será exibido dentro de uma janela no IDE. Se não puder ser incorporada, uma janela de nível superior é criada.  
  
 hierarquia  
 Árvore de nós, cada nó associado a um conjunto de propriedades.  
  
 componente de nível superior independente  
 Um componente que usa uma janela de nível superior sem janela restrita e pode funcionar efetivamente como uma janela de aplicativo autônomo, mas é implementado como um objeto no processo. Portanto, um componente independente de nível superior deve coordenar modalidade e serviços de loop de mensagem com o IDE. Objetos de processo não tem seu próprio loop de mensagem.  
  
 provedor de informações  
 O provedor de informações é um módulo que pode pesquisar palavras-chave e retornar uma lista de tópicos, na forma de `IVsUserContextItem` objetos. Para fornecer itens de palavra-chave F1 e pesquisa para o provedor de informações, registrar o arquivo de Ajuda compilado (. Nos formatos HxS) com o sistema. Os tópicos da Ajuda nesses arquivos são usados para fornecer a lista de tópicos exibida na janela de ajuda dinâmica e mostra se o usuário pressiona F1.  
  
 componente no local  
 Um objeto de VSPackage que implementa o `IOleInPlaceComponent` interface para gerenciar uma janela visualmente contido em uma janela de documentos pertencente o IDE. Componentes no local não participam padrão-mesclagem de menus OLE; em vez disso, eles se integram seus elementos de interface do usuário no IDE.  
  
 Há dois tipos de componentes no local: conectada in-loco componentes e controles de componente.  
  
 Conectada in-loco componentes têm menus, barras de ferramentas e comandos que são totalmente integrados a interface do usuário do IDE, que aparecem como se elas foram criadas diretamente no IDE.  
  
 Controles de componente não tem qualquer um dos seus próprios elementos de interface de usuário integrados ao IDE; em vez disso, use as barras de ferramentas, comandos e menus do IDE. Por exemplo, o comando em negrito pode ser usado como negrito uma palavra selecionada em um controle rich text inserido em um formulário. No entanto, os controles de componente podem solicitar que elementos de interface do usuário específico do componente instalados dinamicamente seja exibido.  
  
 serviço de linguagem  
 Um conjunto de objetos que permite aos desenvolvedores VSPackage implementar recursos de editores de códigos de idioma do computador, como marcação e coloração de texto.  
  
 Projeto de arquivos diversos  
 Projeto usado para hospedar arquivos abertos que não estão em qualquer projeto. A lista de itens no projeto não é persistente.  
  
 projeto  
 Projetos são compostos de objetos de hierarquia ou COM os objetos que implementam o `IVsHierarchy` interface.  
  
 designer de projeto específico ou editor  
 Um designer que não pode ser usado independentemente do tipo de projeto. Todos os designers específicos do projeto insira suas informações de fábrica do Editor do registro. O IDE, em seguida, pode instanciar o designer sempre que um determinado tipo de arquivo é aberto em um projeto específico.  
  
 janela de tipo de projeto  
 Uma janela que rastreia constantemente a hierarquia do projeto ativo e o item do contexto global de seleção. O tipo de projeto windows usa o `SVsTrackSelectionEx` serviço para alertar o IDE de alterações e para exibir comentários para o usuário. Gerenciador de soluções é um exemplo de uma janela de tipo de projeto.  
  
 Janela de Propriedades  
 Navegador de propriedade anteriormente.  
  
 projetos baseados em referências  
 Projeto que não exigem os arquivos para o projeto esteja no mesmo diretório. Em vez disso, referências a arquivos de outros diretórios não relacionados são armazenadas e mantidas pelo próprio projeto.  
  
 tabela de documento em execução  
 Estrutura interna que o IDE mantém a lista de todos os documentos abertos no momento. Essa lista inclui todos os documentos abertos na memória, independentemente se os documentos estão sendo editados atualmente. Um documento é qualquer item que é salvo, inclusive procedimentos armazenados abertos em um editor, arquivos em um projeto ou o arquivo de projeto principal (por exemplo, arquivos *. vcproj).  
  
 contexto de seleção  
 Dados que faz parte dos detalhes de cada janela no IDE e são usados para rastrear as seleções ativas. Contexto de seleção consiste em:  
  
-   Ponteiro para o `IVsHierarchy` interface da hierarquia do projeto  
  
-   Identificador de item do item de projeto.  
  
-   Ponteiro para o `ISelectionContainer` interface fornecendo acesso às propriedades de objetos ativos.  
  
-   Matriz de valores de elemento.  
  
 serviço  
 Um contrato para um conjunto de interfaces que residem em um único objeto COM. Quando você cria um serviço, que é identificado por um GUID, você definir o conjunto de interfaces COM que executa o serviço. Objetos COM usam serviços para se comunicar entre si.  
  
 solução  
 Grupo de projetos relacionados com o qual um usuário trabalha.  
  
 designer padrão  
 Um designer pode ser usado independentemente do tipo de projeto. Todos os designers padrão Insira suas informações de fábrica do Editor do registro. O IDE, em seguida, pode instanciar o designer sempre que um arquivo com uma extensão específica for aberto. Os dados devem persistir em um arquivo.  
  
 editor padrão  
 Editor que pode ser usada independentemente de qualquer tipo de projeto específico. Esses editores tem EditorFactories registrados no registro. Isso permite que o IDE localizar e invocar o editor.  
  
 editor padrão do sistema operacional  
 Uma inserção não é Visual Studio específico. Ele é registrado usando as chaves conhecidas do Win32 (por exemplo, o Gerenciador de Win32 sabe como chamar). Se tal um editor pode ser incorporado, o editor ainda aparecerá em seu lugar no IDE. Caso contrário, uma janela de nível superior é criada para esses editores.  
  
 recipiente subcontexto  
 Um `IVsUserContext` objeto vinculado a um recipiente de contexto. Esse objeto contém palavras-chave de pesquisa, palavras-chave F1 e os atributos de uma seleção em um componente do IDE. Exemplos de subcontexto incluem um comando em uma janela de ferramenta ou uma palavra-chave em um editor.  
  
 Lista de tarefas  
 Janela de ferramenta que é implementada pelo IDE e exibe uma lista de tarefas ativas.  
  
 buffer de texto  
 Nome comum do objeto `VSTextBuffer`.  
  
 Exibição de texto  
 Nome comum do objeto `VSTextView`.  
  
 componente de nível superior da ferramenta  
 Um componente que funciona como uma janela pop-up sem janela restrita, coordenar totalmente com a interface de usuário do IDE. Como componentes independentes de nível superior, os componentes de nível superior da ferramenta também devem coordenar modalidade e serviços de loop de mensagem com o IDE.  
  
 componente de nível superior  
 Um objeto de VSPackage que gerencia uma janela de nível superior sem janela restrita em vez da área cliente de uma janela do IDE. Componentes de nível superior é implementar o `IOleComponent` interface para tirar proveito dos serviços de loop de mensagem, como acesso de tempo ocioso.  
  
 Interface do usuário ativo  
 Um objeto de VSPackage que está visível e tem o foco no momento.  
  
 Hierarquia de interface do usuário  
 Um objeto COM que implementa o `IVsUIHierarchy` interface para permitir a exibição de uma hierarquia. A janela de hierarquia de interface do usuário implementa o `ISelectionContainer` da interface para atualizar a janela Propriedades; outras janelas de tipo de projeto podem usar essa implementação, se desejado.  
  
 VSCT  
 Tabela de comando do Visual Studio. O arquivo. VSCT contém informações sobre o posicionamento e comportamentos de menus, barras de ferramentas e comandos no formato XML.  
  
 VSPackage  
 Uma parte pode ser instalada de softwares que estendem o IDE do Visual Studio ao contribuir com um ou mais dos seguintes: interface do usuário, serviços, tipos de projeto ou editor/designer. Um VSPackage consiste em um objeto COM que implementa o `IVsPackage` interface e um ou mais outros objetos que implementam interfaces para oferecer suporte a seleção e outros recursos. Além disso, um VSPackage possui requisitos de registro específico.
