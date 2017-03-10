---
title: "Passo a passo: Personalizando a configura&#231;&#227;o do Item de caixa de ferramentas dinamicamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Caixa de ferramentas [Visual Studio SDK], adicionando controles (formatos personalizados)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# Passo a passo: Personalizando a configura&#231;&#227;o do Item de caixa de ferramentas dinamicamente
Este passo a passo mostra como um VSPackage gerenciado pode fornecer suporte a configuração dinâmica do <xref:System.Drawing.Design.ToolboxItem> objetos.  
  
> [!NOTE]
>  A maneira mais simples de adicionar controles personalizados à caixa de ferramentas é usar os modelos de controle de caixa de ferramentas incluídas no SDK do Visual Studio. Este tópico está relacionado ao desenvolvimento de ferramentas avançadas.  
>   
>  Para obter mais informações sobre como criar controles de caixa de ferramentas, usando os modelos, consulte [Como: criar um controle de caixa de ferramentas que usa o Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) e [Criando um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Este passo a passo orienta você pelas seguintes etapas:  
  
1.  Adicionar e registrar todos **Toolbox** controles nos objetos de VSPackage usando o <xref:System.ComponentModel.ToolboxItemAttribute> e <xref:System.Drawing.ToolboxBitmapAttribute> classes.  
  
2.  Crie os seguintes dois controles e adicionar ícones para cada um para o **Toolbox**:  
  
    -   Um controle que declara um padrão associado <xref:System.Drawing.Design.ToolboxItem>.  
  
    -   Um controle que declara um personalizado associado **ferramentas** item que é derivado de <xref:System.Drawing.Design.ToolboxItem> classe.  
  
3.  Escrever uma implementação de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, e registrá\-lo seguindo as seguintes ações:  
  
    1.  Definindo uma classe de filtro que deriva de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> classe e especifica o <xref:System.Drawing.Design.ToolboxItem> instâncias que essa implementação atuará na.  
  
    2.  Aplicando um <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>, que faz referência à classe filtro, a classe que implementa o <xref:Microsoft.VisualStudio.Shell.Package> classe para o VSPackage.  
  
4.  Registre o VSPackage como um provedor de <xref:System.Drawing.Design.ToolboxItem> objetos aplicando o <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> para a classe que implementa o <xref:Microsoft.VisualStudio.Shell.Package> classe para o VSPackage.  
  
5.  No pacote de tempo de carregamento, usar a reflexão para gerar uma lista de todos os <xref:System.Drawing.Design.ToolboxItem> objetos que fornece o VSPackage.  
  
6.  Criar um manipulador para o <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> e <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> eventos. Isso garante que o VSPackage <xref:System.Drawing.Design.ToolboxItem> objetos são carregados corretamente.  
  
7.  Implementar um comando sobre o VSPackage para forçar a reinicialização do **Toolbox**.  
  
## Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do pacote do Visual Studio pode ser encontrado em três locais diferentes de **novo projeto** caixa de diálogo:  
  
1.  Em extensibilidade do Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2.  Sob c\# extensibilidade. O idioma padrão do projeto é c\#.  
  
3.  Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C\+\+.  
  
## Criando um VSPackage gerenciado  
 Conclua os procedimentos a seguir para criar um VSPackage gerenciado.  
  
#### Para criar um VSPackage gerenciado para fornecer itens da caixa de ferramentas  
  
1.  Crie um VSPackage chamado `ItemConfiguration`. Para obter mais informações, consulte [Passo a passo: Criando um comando de Menu usando o modelo de pacote do Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  No **Visual Studio Package** modelo, adicione um comando de menu.  
  
     Nomeie o comando `Initialize ItemConfigurationVB` para o Visual Basic ou `Initialize ItemConfigurationCS` para Visual c\#.  
  
3.  Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], adicione os seguintes namespaces à lista de namespaces importados no projeto gerado:  
  
    -   Company.ItemConfiguration  
  
    -   Sistema  
  
    -   System.ComponentModel  
  
    -   System. Drawing  
  
    -   System.Windows.Forms  
  
4.  Adicione uma referência para o <xref:System.Drawing.Design?displayProperty=fullName> componente do .NET Framework.  
  
 Se você seguir este passo a passo para mais de um idioma, você deve atualizar o projeto para resolver a ambiguidade os assemblies gerados.  
  
#### Para resolver a ambiguidade do Visual Basic e Visual c\# VSPackages  
  
1.  Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    1.  Abra as propriedades do projeto e selecione o **aplicativo** guia.  
  
         Altere o nome de assembly para `ItemConfigurationVB`, e altere o namespace padrão para `Company.ItemConfigurationVB`.  
  
    2.  Selecione o **referências** guia.  
  
         Atualize a lista de namespaces importados.  
  
         Remova Company.ItemConfiguration.  
  
         Adicione Company.ItemConfigurationVB.  
  
2.  Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  Abra as propriedades do projeto e selecione o **aplicativo** guia.  
  
         Altere o nome de assembly para `ItemConfigurationCS`, e altere o namespace padrão para `Company.ItemConfigurationCS`.  
  
    2.  Abra a classe ItemConfigurationPackage no editor de códigos.  
  
         Usar as ferramentas de refatoração para renomear o namespace existente, clique no nome do namespace existente, `ItemConfiguration`, aponte para **Refatorar**, e, em seguida, clique em **Renomear**. Altere o nome para `ItemConfigurationCS`.  
  
3.  Salve todas as alterações.  
  
#### Para testar o código gerado  
  
1.  Compilar e iniciar o VSPackage na seção experimental do Visual Studio.  
  
2.  Sobre o **ferramentas** menu, clique em **inicializar VB do Item de configuração** ou **inicializar CS do Item de configuração**.  
  
     Isso abre uma caixa de mensagem que contém o texto que indica que o manipulador de item de menu do pacote foi chamado.  
  
3.  Feche a versão experimental do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Criando controles de caixa de ferramentas  
 Nesta seção, você pode criar e registrar um controle de usuário, `Control1`, que declara um padrão associado **Toolbox** item. Criar e registrar um segundo controle de usuário, também `Control2`, e um personalizado associado **ferramentas** item, `Control2_ToolboxItem`, que é derivado de <xref:System.Drawing.Design.ToolboxItem> classe. Para obter mais informações sobre como criar controles de formulários do Windows e <xref:System.Drawing.Design.ToolboxItem> classes, consulte [Desenvolvendo controles dos Windows Forms na hora de design](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### Criar padrão e itens de caixa de ferramentas personalizado  
  
1.  Use as instruções em [Instruções passo a passo: Itens de caixa de ferramentas realiza o carregamento automático](../Topic/Walkthrough:%20Autoloading%20Toolbox%20Items.md) para criar um padrão **Toolbox** item e um personalizado **Toolbox** item, da seguinte maneira.  
  
    1.  Conclua o procedimento "para criar um **Toolbox** controle que será usado com um padrão Toolbox ­." Atualizar o <xref:System.ComponentModel.DescriptionAttribute> para fazer referência a esse projeto.  
  
         O código resultante para o `Control1` classe deve se parecer com o código a seguir.  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  Conclua o procedimento "para criar um **Toolbox** controle para o uso de uma classe personalizada derivada de Toolbox ­." Atualizar o <xref:System.ComponentModel.DescriptionAttribute> para fazer referência a esse projeto.  
  
         O código resultante para o `Control2` e `Control2_ToolboxItem` classes devem se parecer com o código a seguir.  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  Salve os arquivos.  
  
## Inserção de ícones de Bitmap  
 O <xref:System.Drawing.ToolboxBitmapAttribute> atributo é aplicado a cada controle especifica qual ícone para associar ao controle. Criar bitmaps em ambos os controles e nomeá\-los da seguinte maneira:  
  
-   `Control1.bmp`, para o `Control1` classe.  
  
-   `Control2.bmp`, para o `Control2` classe.  
  
#### Para inserir um ícone de bitmap de um item de caixa de ferramentas  
  
1.  Adicione um novo bitmap ao projeto, da seguinte maneira:  
  
    1.  Em **Solution Explorer**, com o botão direito no projeto de VSPackage, aponte para **Add**, e, em seguida, clique em **Novo Item**.  
  
    2.  No **Add New Item** caixa de diálogo, selecione **arquivo Bitmap**, e digite o nome do bitmap.  
  
2.  Use o editor de bitmap para criar um ícone de 16x16, da seguinte maneira.  
  
    1.  Sobre o **exibição** menu, clique em **janela propriedades**.  
  
    2.  No **propriedades** janela, defina **Altura** e **largura** para 16.  
  
    3.  Use o editor para criar a imagem do ícone.  
  
3.  Em **Solution Explorer**, clique no item de bitmap e, em seguida, clique em **propriedades**.  
  
4.  Definir o **Build Action** propriedade **Embedded Resource**.  
  
5.  Salve todos os arquivos abertos.  
  
## Adicionar um provedor de configuração dinâmica de ferramentas  
 Nesta seção, você pode criar e registrar uma classe que implementa o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> interface. Essa classe é instanciada e usada pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\) para configurar **Toolbox** controles.  
  
> [!NOTE]
>  Porque o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente cria uma instância da implementação do <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, não implemente o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> interface na classe que implementa <xref:Microsoft.VisualStudio.Shell.Package> para um VSPackage.  
  
#### Para criar e registrar um objeto de configuração do controle de caixa de ferramentas  
  
1.  Em **Solution Explorer**, adicionar uma classe ao projeto ItemConfiguration e nomeie\-o `ToolboxConfig`.  
  
2.  Adicione as seguintes instruções de namespace ao arquivo.  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  Verifique se o `ToolboxConfig` classe é `public` e implementa o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> interface.  
  
4.  Aplicar um <xref:System.Runtime.InteropServices.GuidAttribute> e um <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> para o `ToolboxConfig` classe`.`  
  
    -   Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], use um nome de assembly de `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"`.  
  
    -   Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], use um nome de assembly de `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"`.  
  
     Fazer isso restringe a `ToolboxConfig` classe para trabalhar em <xref:System.Drawing.Design.ToolboxItem> objetos que são fornecidos pelo assembly que contém o VSPackage atual.  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     Você pode gerar um GUID, clicando em **criar GUID** sobre o **ferramentas** menu. Selecione **o formato com colchetes**, clique em **cópia**, e, em seguida, cole o GUID em seu código. alterar a palavra\-chave `GUID` para `Guid`.  
  
5.  Implementar o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> método o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> interface para que o método funciona somente em dois <xref:System.Drawing.Design.ToolboxItem> classes, `Control1` e `Control2`.  
  
     A implementação de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> aplica\-se a instâncias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> para os dois <xref:System.Drawing.Design.ToolboxItem> objetos para que:  
  
    -   O <xref:System.Drawing.Design.ToolboxItem> é implementado por `Control1` só está disponível na **Toolbox** para designers que tratam <xref:System.Windows.Forms.UserControl> objetos.  
  
    -   O <xref:System.Drawing.Design.ToolboxItem> é implementado por `Control2` não está disponível na **Toolbox** para designers que tratam <xref:System.Windows.Forms.UserControl> objetos.  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## Modificando a implementação de VSPackage  
 A implementação padrão de VSPackage fornecida pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de pacote deve ser modificado para fazer o seguinte:  
  
-   Registrar como um **Toolbox** provedor de itens.  
  
-   Registrar a classe que fornece a dinâmica **Toolbox** configuração de controle para o VSPackage.  
  
-   Use o <xref:System.Drawing.Design.ToolboxService> para carregar todos os <xref:System.Drawing.Design.ToolboxItem> objetos que são fornecidos pelo assembly de VSPackage.  
  
-   Lidar com <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> e <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> eventos.  
  
#### Para modificar a implementação de pacote para um provedor de item de caixa de ferramentas sobre o VSPackage  
  
1.  Abra a classe ItemConfigurationPackage no editor de códigos.  
  
2.  Modificar a declaração do `ItemConfigurationPackage` classe, que é a implementação da <xref:Microsoft.VisualStudio.Shell.Package> classe na solução.  
  
    1.  Adicione as seguintes instruções de namespace ao arquivo.  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  Para registrar o VSPackage como fornecendo **Toolbox** itens, aplicar um <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> ao pacote. Para registrar o `ToolboxConfig` da classe como fornecendo uma **Toolbox** controlam a configuração dinâmica, aplicar um <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> ao pacote.  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  O único argumento de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> é a versão do <xref:System.Drawing.Design.ToolboxItem> fornecido pelo VSPackage. Ao alterar esse valor, você força o IDE para carregar o VSPackage, mesmo se tiver uma versão em cache anteriormente do <xref:System.Drawing.Design.ToolboxItem>.  
  
    3.  Crie dois novos `private` campos de `ItemConfiguration` classe, da seguinte maneira:  
  
         Um <xref:System.Collections.ArrayList> membro, chamado `ToolboxItemList`, para manter uma lista da <xref:System.Drawing.Design.ToolboxItem> objetos que o `ItemConfiguration` classe gerencia.  
  
         Um <xref:System.String>, denominado `CategoryTab`, que contém o **Toolbox** guia é usado para armazenar o <xref:System.Drawing.Design.ToolboxItem> objetos que o `ItemConfiguration` classe gerencia.  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     O resultado desta modificação se parece com o código a seguir:  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  Definir um `OnRefreshToolbox` método para manipular o <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> e <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> eventos.  
  
     O `OnRefreshToolbox` método usa a lista de <xref:System.Drawing.Design.ToolboxItem> objetos contidos no `ToolboxItemList` campo e faz o seguinte:  
  
    -   Remove todos os <xref:System.Drawing.Design.ToolboxItem> objetos do **Toolbox** guia é definido pelo `CategoryTab` campo.  
  
    -   Adiciona o **Toolbox** guia novas instâncias de todos os <xref:System.Drawing.Design.ToolboxItem> objetos listados no `ToolboxItemList` campo.  
  
    -   Conjuntos de **Toolbox** guia como a guia ativa.  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], no construtor, registrar o `OnRefreshToolbox` método como o manipulador de eventos para o <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> e <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> eventos.  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  Modificar o `Initialize` método `ItemConfigurationPackage` para preencher o `ToolboxItemList` campo chamando o <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> método do <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName> classe. O **Toolbox** service obtém todos os a **Toolbox** item classes definidas no assembly atualmente em execução. O `ToolboxItemList` campo é usado pelo **Toolbox** manipuladores de eventos para carregar o **Toolbox** itens.  
  
     Adicione o seguinte código ao final do `Initialize` método.  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  Como um exercício, um pode desenvolver um mecanismo para teste da versão de VSPackage ou os itens e atualizar somente se a versão de VSPackage foi alterado ou se a versão de <xref:System.Drawing.Design.ToolboxItem> foi alterado.  
  
## Inicializando a caixa de ferramentas  
  
#### Para implementar um comando para inicializar a caixa de ferramentas  
  
-   No `ItemConfigurationPackage` da classe, altere o `MenuItemCallBack` método, que é o manipulador de comandos do item de menu.  
  
     Substituir a implementação existente do `MenuItemCallBack` método usando o código a seguir:  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## Criar e executar a solução  
 É possível utilizar o produto deste passo a passo usando uma instância do Visual Studio que está em execução no hive experimental.  
  
#### Para utilizar este passo a passo  
  
1.  No Visual Studio, no **criar** menu, clique em **recompilar solução**.  
  
2.  Pressione F5 para iniciar uma segunda instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no hive do registro experimental.  
  
     Para obter mais informações sobre como usar o hive experimental, consulte [A instância Experimental](../extensibility/the-experimental-instance.md).  
  
3.  Clique o **ferramentas** menu.  
  
     Um comando chamado **inicializar ItemConfiguration VB** ou **inicializar ItemConfiguration CS** aparece na parte superior do menu, junto com um ícone que tem o número 1.  
  
4.  Criar um novo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aplicativo Windows Forms.  
  
     Um <xref:System.Windows.Forms.Form>\-designer com base aparece.  
  
5.  Adicione um controle de usuário ao projeto.  
  
     Um designer de controle de usuário é exibida.  
  
6.  PIN do **Toolbox** abrir e alternar entre os modos de exibição de design de dois.  
  
     Observe que que **Toolbox** item está visível e qual deles está oculto depende de que o designer tem o foco.  
  
7.  Arraste o primeiro **Toolbox** item no controle do usuário para adicionar uma instância de `Control1` ao controle de usuário.  
  
8.  Arraste a segunda **Toolbox** item para o formulário para adicionar uma instância de `Control2` ao formulário.  
  
9. Compile o aplicativo do Windows.  
  
     O controle de usuário para o aplicativo agora está disponível na **Toolbox**.  
  
10. Adicionar o controle de usuário do aplicativo para o formulário e recompilar o aplicativo e executá\-lo.  
  
     Quando o aplicativo é executado, clique em cada controle no formulário para abrir a caixa de mensagem associada.  
  
## Análise da implementação  
 Porque o `assemblyFilter` parâmetro estiver presente no <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> construtor da classe, somente <xref:System.Drawing.Design.ToolboxItem> objetos no assembly produzido nesse passo a passo são acionados pelo <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> método o `ToolboxConfg` classe.  
  
 Portanto, sempre que o **ItemConfiguration Walkthrough** categoria está ativa no **Toolbox**, o <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> método do `ToolboxConfg` classe é chamada, e <xref:System.ComponentModel.ToolboxItemFilterAttribute> instâncias são aplicadas no <xref:System.Drawing.Design.ToolboxItem> objetos que são implementados por `Control1` e `Control2`.  
  
## Consulte também  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)   
 [Registrar os recursos de suporte da caixa de ferramentas](../misc/registering-toolbox-support-features.md)   
 [Desenvolvimento de controle de caixa de ferramentas avançadas](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Explicações passo a passo de ferramentas](../misc/toolbox-walkthroughs.md)