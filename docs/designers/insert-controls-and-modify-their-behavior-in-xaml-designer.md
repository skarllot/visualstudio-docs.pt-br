---
title: "Inserir controles e modificar seu comportamento no XAML Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Inserir controles e modificar seu comportamento no XAML Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Controles permitem aos usuários interagir com seu aplicativo. Você pode usá\-los para coletar informações e executar ações como animar um objeto ou consultar uma fonte de dados.  
  
 **Neste tópico:**  
  
-   [Adicionar controles à prancheta](#Insert)  
  
-   [Faça controles fazer coisas](#Modify)  
  
##  <a name="Insert"></a> Adicionar controles à prancheta  
 Você pode arrastar controles do **ativos** painel para o **prancheta**, e, em seguida, modificá\-las no **propriedades** janela.  
  
 ![Blend &#45; Assets &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend\_AssetsFlipView\_XAML")  
  
 Esses vídeos mostram como usar alguns dos controles mais comuns.  
  
|Controle|Assista a um vídeo curto|  
|--------------|------------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c\-0b2b\-4253\-ac57\-b86fcb8c9591")|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar os controles](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779\-a68f\-436b\-b834\-a91b7995a3ec")|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar um botão](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963\-00f7\-4a33\-abcd\-b0849edebada")|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar imagens a um textblock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92\-3c74\-4218\-815c\-e98c930ac189")|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar um controle deslizante com uma dica de ferramenta](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f\-a27e\-4a8f\-95aa\-8a4e8b4ee7be")|![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabalhar com um GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### Tornar um controle fora de uma imagem, forma ou caminho  
 Você pode transformar qualquer objeto em um controle.  
  
 ![Blend Make Into Control dialog box](../designers/media/blend_makeintocontrol_xaml.png "blend\_MakeIntoControl\_XAML")  
  
 Por exemplo, imagine uma imagem de uma televisão no centro da página. Você pode fazer controles sem imagens pequenas que se parecem com botões de televisão. Em seguida, os usuários poderiam clique esses botões para alterar o canal.  
  
 Isso é possível porque os botões agora são controles. Com controles, você pode responder às interações do usuário; Nesse caso, quando o usuário clica em um botão.  
  
 Para criar um controle, selecione um objeto. Em seguida, no **ferramentas** menu, clique em **transformar controle**.  
  
##  <a name="Modify"></a> Faça controles fazer coisas  
 Controles podem executar ações quando os usuários interagem com eles. Por exemplo, eles podem iniciar uma animação, atualizar uma fonte de dados ou reproduzir um vídeo.  
  
 Use *gatilhos*, *comportamentos*, e *eventos* para tornar os controles fazer coisas.  
  
### Gatilhos  
 Um *gatilho* altere uma propriedade ou executa uma tarefa em resposta a um evento ou uma alteração em outra propriedade. Por exemplo, você pode alterar a cor de um botão quando os usuários passar o mouse sobre ele.  
  
 ![O painel "Gatilhos"](../designers/media/custom_button_blend_propertytriggerinfo.png "custom\_button\_blend\_PropertyTriggerInfo")  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar um gatilho de propriedade](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### Comportamentos  
 Um *comportamento* é um pacote reutilizável de código. Ele pode fazer um pouco mais de alterar as propriedades. Ele pode realizar ações como um serviço de dados de consulta. Blend vem com uma pequena coleção deles, mas você pode adicionar mais. Arraste um comportamento para qualquer objeto na sua prancheta e personalizar o comportamento definindo propriedades.  
  
 ![FluidMoveBehavior in the Properties panel](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4\_FluidMoveBehaviorProperties\_Sample")  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [dicas de mesclagem: Introdução ao uso de comportamentos parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### Eventos  
 Para máxima flexibilidade, manipular um *evento*. Você precisará escrever algum código.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Adicionar um evento de Mouse](https://www.youtube.com/watch?v=2PMxAlb-x_E).