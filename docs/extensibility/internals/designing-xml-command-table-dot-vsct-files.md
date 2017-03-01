---
title: Criar tabela de comando XML (. Arquivos VSCT) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
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
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>Criar tabela de comando XML (. Arquivos de VSCT)
Um arquivo de tabela (VSCT) do comando XML descreve o layout e a aparência de itens do comando para um VSPackage. Comando itens incluem caixas de combinação, botões, menus, barras de ferramentas e grupos de itens do comando. Este tópico descreve arquivos de tabela do comando XML, como eles afetam os menus e itens de comando e como criá-los.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>O arquivo. VSCT, Menus, grupos e comandos  
 arquivos. VSCT são organizados em torno de comandos, menus e grupos de comando. Marcas XML no arquivo. VSCT representam cada um desses itens, juntamente com outros itens associados, como botões de comando, o posicionamento de comando e bitmaps.  
  
 Quando você cria um novo VSPackage executando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelo de pacote, o modelo gera um arquivo. VSCT com os elementos necessários para um comando de menu, a janela da ferramenta ou o editor personalizado, dependendo de suas seleções. Esse arquivo. VSCT, em seguida, pode ser modificado para atender aos requisitos de um VSPackage específico. Para obter exemplos de como modificar um arquivo. VSCT, consulte os exemplos [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Para criar um arquivo. VSCT em branco, consulte [como: criar um. Arquivo VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Uma vez criado, adicione elementos XML, atributos e valores para o arquivo para descrever o layout do item de comando. Para um esquema XML detalhado, consulte o [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Diferenças entre arquivos .ctc e VSCT  
 Embora o significado por trás de marcas XML em um arquivo. VSCT é os mesmos que aqueles de agora preteridos .ctc formato de arquivo, sua implementação é um pouco diferente.  
  
-   O novo ** \<extern >** marca é onde você fazer referência a outros arquivos. h para ser compilado, como aquelas para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
-   Embora o suporte a arquivos. VSCT o **/ incluem** instrução, como arquivos de .ctc, ele também apresenta um novo \< **importar >** elemento. A diferença é, **/ incluem** traz **todas as** das informações, mas \< **importar >** traz apenas os nomes.  
  
-   Enquanto .ctc arquivos requerem um arquivo de cabeçalho no qual você define suas diretivas de pré-processador, um não é necessário para os arquivos. VSCT. Em vez disso, colocar suas diretivas na tabela de símbolo, localizada no ** \<símbolo >** elementos, localizados na parte inferior do arquivo. VSCT.  
  
-   recurso de arquivos. VSCT um ** \<anotação >** marca, que permite que você insira informações que desejar, como anotações ou até mesmo imagens.  
  
-   Valores são armazenados como atributos no item.  
  
-   Sinalizadores de comando podem ser armazenadas individualmente ou empilhados.  IntelliSense, no entanto, não funciona em sinalizadores de comando empilhadas. Para obter mais informações sobre sinalizadores de comando, consulte o [comando sinalizador elemento](../../extensibility/command-flag-element.md).  
  
-   Você pode especificar vários tipos, como listas suspensas de divisão, combinações, etc.  
  
-   GUIDs não validar.  
  
-   Cada elemento de interface do usuário tem uma cadeia de caracteres que representa o texto que é exibido com ele.  
  
-   Pai é opcional. Se omitido, será usado o valor "Desconhecido" grupo".  
  
-   O argumento de ícone é opcional.  
  
-   A seção de bitmap – o mesmo que um .ctc de arquivos, exceto que agora você pode especificar um nome de arquivo por meio de href que será obtido pelo compilador vsct.exe em tempo de compilação.  
  
-   ResID – a ID de recurso de bitmap antigo pode ser usada e ainda funciona da mesma forma .ctc arquivos.  
  
-   HRef - um novo método que permite que você especifique um nome de arquivo para o recurso de bitmap. Ele pressupõe que são usados, assim você pode omitir a seção usada. O compilador primeiro procurar recursos locais para o arquivo, em seguida, em qualquer compartilhamento de rede e nenhum recurso definido pela opção /I.  
  
-   KeyBinding – Você não precisa especificar um emulador. Se você especificar um, o compilador assumirá que o editor e o emulador são os mesmos.  
  
-   Keychord – foi descartada. O novo formato é Key1, Mod1, Key2, Mod2.  Você pode especificar um caractere, hexadecimal ou constante VK.  
  
 O novo compilador, vsct.exe, compila arquivos .ctc e VSCT. O compilador ctc.exe antiga, no entanto, não reconhece nem compilar arquivos. VSCT.  
  
 Você pode usar o compilador vsct.exe para converter um arquivo .cto existente em um arquivo. VSCT. Para obter mais informações sobre isso, consulte [como: criar um. Arquivo VSCT de uma já existente. Arquivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Os elementos do arquivo. VSCT  
 A tabela de comando tem a hierarquia e os elementos a seguir:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) — representa todos os comandos, grupos de menus e menus associados com o VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) — faz referência a todos os arquivos. h externo que deseja mesclar com o arquivo. VSCT.  
  
 [Incluir elemento](../../extensibility/include-element.md) — faz referência a todos os arquivos adicionais de cabeçalho (. h) você deseja compilar juntamente com o arquivo your.vsct. Um arquivo. VSCT pode incluir arquivos. h que contém constantes que definem os comandos, grupos de menus e menus que fornece o IDE ou outro VSPackage.  
  
 [Comandos elemento](../../extensibility/commands-element.md) — representa todos os comandos individuais que podem ser executados. Cada comando tem os seguintes elementos quatro filho:  
  
 [Elemento de menus](../../extensibility/menus-element.md) — representa todos os menus e barras de ferramentas do VSPackage. Menus são contêineres para grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) — representa todos os grupos de VSPackage. Grupos são coleções de comandos individuais.  
  
 [Botões de elemento](../../extensibility/buttons-element.md) — representa todos os botões de comando e itens de menu no VSPackage. Botões são os controles visuais que podem ser associados a comandos.  
  
 [Elemento de bitmaps](../../extensibility/bitmaps-element.md) — representa todos os bitmaps de todos os botões de VSPackage. Os bitmaps são imagens que são exibidas ao lado ou nos botões de comando, dependendo do contexto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) — indica outros locais onde os comandos individuais devem ser colocados nos menus do VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) — Especifica se um comando em todos os exibe vezes ou somente em determinados contextos, como quando uma caixa de diálogo específica ou janela é exibida. Menus e comandos que têm um valor para esse elemento serão exibido apenas quando o contexto especificado está ativo. O comportamento padrão é exibir o comando em todos os momentos.  
  
 [Elemento KeyBindings](../../extensibility/keybindings-element.md) — Especifica quaisquer associações de teclas para os comandos. Ou seja, um ou mais combinações de teclas que devem ser pressionadas para executar o comando, como **CTRL + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) — Informs o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente que, embora o comando especificado é implementado por outro código, quando o VSPackage atual está ativo, ele fornece a implementação do comando.  
  
 `Symbols Element`– Contém os nomes de símbolos e IDs de GUID para todos os seus comandos no pacote.  
  
## <a name="vsct-file-design-guidelines"></a>. Diretrizes de Design do arquivo VSCT  
 Para criar com êxito um arquivo. VSCT, siga estas diretrizes.  
  
-   Comandos podem ser colocados apenas em grupos, grupos podem ser colocados somente nos menus e menus podem ser colocados apenas em grupos. Menus só são exibidos no IDE, grupos e comandos não são.  
  
-   Submenus não podem ser atribuídos diretamente a um menu, mas devem ser atribuídos a um grupo, que por sua vez é atribuído a um menu.  
  
-   Comandos, submenus e grupos podem ser atribuídos a um grupo de paternidade ou menu usando o campo pai da sua diretiva de definição.  
  
-   Organização de uma tabela de comando somente por meio de campos pai nas diretivas tem uma limitação significativa. As diretivas que definem objetos podem levar um argumento de apenas um pai.  
  
-   Reutilização de comandos, grupos ou submenus requer o uso de uma nova diretiva para criar uma nova instância do objeto com seu próprio `GUID:ID` par.  
  
-   Cada `GUID:ID` par deve ser exclusivo. Reutilizar um comando que, por exemplo, foi colocado em um menu, uma barra de ferramentas ou em um menu de contexto, é tratada pelo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   Comandos e submenus também podem ser atribuídos a vários grupos e grupos podem ser atribuídos a vários menus usando o [comandos elemento](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notas do arquivo VSCT  
 Se você fizer alterações em um arquivo. VSCT depois tanto compilá-lo e colocá-lo em uma DLL satélite nativa, você deve executar **devenv.exe /setup /nosetupvstemplates**. Isso força os recursos de VSPackage especificados no registro experimental para ser lidos novamente e o banco de dados interno que descreve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seja recriado.  
  
 Durante o desenvolvimento, é possível para vários projetos de VSPackage seja criado e registrado no hive do registro experimental que pode levar a bagunça confusa no IDE. Para corrigir isso, você pode redefinir o hive experimental para as configurações padrão para remover todas as marcas VSPackages e as alterações que fez o IDE. Para redefinir o hive experimental, use a ferramenta CreateExpInstance.exe que vem com o SDK do Visual Studio. Você pode encontrá-lo em  
  
 **% PROGRAMFILES (x86) %\Visual Studio \<versão > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Executar a ferramenta usando a linha de comando **CreateExpInstance /Reset**. Lembre-se de que essa ferramenta remove o hive experimental todos os VSPackages registrados normalmente não é instalados com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md)
