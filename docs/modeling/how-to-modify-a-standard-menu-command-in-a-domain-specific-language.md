---
title: "Como: modificar um comando de Menu padrão em uma linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 10
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 571b30e0be9863b20dc1c8abca87940bb21cc344
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Como modificar um comando de menu padrão em uma linguagem específica do domínio
É possível modificar o comportamento de alguns dos comandos padrão que são definidos automaticamente na DSL. Por exemplo, você poderia modificar **Recortar** para que ele exclui informações confidenciais. Para isso, substitua métodos em uma classe de conjunto de comandos. Essas classes são definidas no arquivo CommandSet.cs, no projeto DslPackage e são derivadas de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.</xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>  
  
 Em resumo, para modificar um comando:  
  
1.  [Descubra quais comandos que você pode modificar](#what).  
  
2.  [Criar uma declaração parcial da classe de conjunto apropriado de comando](#extend).  
  
3.  [Substituir os métodos ProcessOnStatus e ProcessOnMenu](#override) para o comando.  
  
 Este tópico explica esse procedimento.  
  
> [!NOTE]
>  Se você quiser criar seus próprios comandos de menu, consulte [como: adicionar um comando ao Menu de atalho](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
##  <a name="a-namewhata-what-commands-can-you-modify"></a><a name="what"></a>Os comandos que você pode modificar?  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>Para descobrir quais comandos podem ser modificados  
  
1.  No `DslPackage` projeto, abra `GeneratedCode\CommandSet.cs`. Esse arquivo c# pode ser encontrado no Gerenciador de soluções, como uma subsidiária da `CommandSet.tt`.  
  
2.  Localizar classes nesse arquivo cujos nomes terminam com "`CommandSet`", por exemplo `Language1CommandSet` e `Language1ClipboardCommandSet`.  
  
3.  Em cada classe de conjunto de comandos, digite "`override`" seguido por um espaço. O IntelliSense mostrará uma lista dos métodos que podem ser substituídos. Cada comando contém um par de métodos cujos nomes começam com "`ProcessOnStatus`" e "`ProcessOnMenu`".  
  
4.  Observe qual das classes de conjunto de comandos contém o comando que deseja modificar.  
  
5.  Feche o arquivo sem salvar as edições.  
  
    > [!NOTE]
    >  Normalmente, é aconselhável não editar arquivos que foram gerados. Qualquer edição será perdida na próxima vez em que os arquivos forem gerados.  
  
##  <a name="a-nameextenda-extend-the-appropriate-command-set-class"></a><a name="extend"></a>Estender a classe de conjunto de comandos adequada  
 Crie um novo arquivo que contenha uma declaração parcial da classe de conjunto de comandos.  
  
#### <a name="to-extend-the-command-set-class"></a>Estender a classe de Conjunto de Comandos  
  
1.  No Gerenciador de Soluções, no projeto DslPackage, abra a pasta GeneratedCode e procure sob CommandSet.tt e abra o arquivo gerado CommandSet.cs. Observe o namespace e o nome da primeira classe que está definida lá. Por exemplo, é possível ver:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  Em **DslPackage**, crie uma pasta chamada **código personalizado**. Nessa pasta, crie um novo arquivo de classe chamado `CommandSet.cs`.  
  
3.  No novo arquivo, grave uma declaração parcial que contenha o mesmo namespace e o nome que a classe parcial gerada. Por exemplo:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **Observação** se você usou o modelo de arquivo de classe para criar o novo arquivo, você deve corrigir o namespace e o nome da classe.  
  
##  <a name="a-nameoverridea-override-the-command-methods"></a><a name="override"></a>Substituir os métodos de comando  
 A maioria dos comandos têm dois métodos associados: O método com um nome como `ProcessOnStatus`… determinará se o comando deve ser visível e habilitado. É chamado sempre que o usuário clicar com o botão direito do mouse no diagrama e deve ser executado rapidamente e não realizar alterações. `ProcessOnMenu`... é chamado quando o usuário clica no comando e deve executar a função do comando. É possível substituir qualquer um dos métodos ou os dois.  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>Para alterar quando o comando é exibido em um menu  
 Substitua o método … método. Esse método deve definir as propriedades Visível e Habilitado de seu parâmetro MenuCommand. Geralmente, o comando examina this.CurrentSelection para determinar se o comando é aplicável aos elementos selecionados e também poderá examinar suas propriedades para determinar se o comando pode ser aplicado em seu estado atual.  
  
 Como guia geral, a propriedade Visível deve ser determinada por quais elementos estão selecionados. A propriedade Habilitado, que determina se o comando é exibido em preto ou cinza no menu, deve depender do estado atual da seleção.  
  
 O exemplo a seguir desabilita o item de menu Excluir quando o usuário selecionar mais de uma forma.  
  
> [!NOTE]
>  Esse método não afeta se o comando está disponível através de um pressionamento de tecla. Por exemplo, desabilitar o item de menu Excluir não impede a invocação do comando através da tecla Delete.  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 É uma boa prática chamar primeiro o método base, para lidar com todos os casos e as configurações pelos quais não houver interesse.  
  
 O método ProcessOnStatus não deve criar, excluir ou atualizar elementos no Armazenamento.  
  
### <a name="to-change-the-behavior-of-the-command"></a>Para alterar o comportamento do comando  
 Substitua o método … método. O exemplo a seguir impede o usuário de excluir mais de um elemento de cada vez, mesmo usando a tecla Delete.  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 Se o código fizer alterações ao Armazenamento, como criar, excluir ou atualizar elementos ou links, será necessário fazer isso dentro de uma transação. Para obter mais informações, consulte [como elementos de modelo de criação e atualização](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Gravando o código dos métodos  
 Os seguintes fragmentos são úteis com frequência dentro desses métodos:  
  
-   `this.CurrentSelection`. A forma que o usuário clicou com o botão direito sempre é incluída nessa lista de formas e conectores. Se o usuário clicar em uma parte em branco do diagrama, o Diagrama será o único membro da lista.  
  
-   `this.IsDiagramSelected()` - `true`Se o usuário clicou em uma parte em branco do diagrama.  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()` - o usuário não selecionou múltiplas formas  
  
-   `this.SingleSelection` - a forma ou o diagrama que o usuário clicou com o botão direito  
  
-   `shape.ModelElement as MyLanguageElement` - o elemento de modelo representado por uma forma.  
  
 Para obter mais informações sobre como navegar entre elementos e sobre como criar objetos e links, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.Design.MenuCommand></xref:System.ComponentModel.Design.MenuCommand>   
 [Escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Como: adicionar um comando ao Menu de atalho](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK – exemplo de diagramas de circuito. DSL ampla personalização](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [Código de exemplo: diagramas de circuito](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

