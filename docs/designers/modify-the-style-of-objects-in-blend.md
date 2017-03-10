---
title: "Modificar o estilo de objetos no Blend | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Modificar o estilo de objetos no Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A maneira mais fácil de personalizar um objeto é definir propriedades no **propriedades** painel.  
  
 Se você quiser reutilizar configurações ou grupos de configurações, crie um recurso pode ser reutilizado.  Isso pode ser um *estilos*, *modelo*, ou algo simples como uma cor personalizada.  Você também pode fazer um controle aparecer diferente com base em seu estado.  Por exemplo, um botão muda para verde quando o usuário clica nele.  
  
 **Neste tópico**:  
  
-   [Pincéis: Modificar a aparência de um objeto](#Brushes)  
  
-   [Estilos e modelos: criar uma aparência consistente entre controles](#Styles)  
  
-   [Estados visuais: Alterar a aparência de um controle com base em seu estado](#Visual)  
  
-   [Recursos: Criar cores, estilos e modelos e reutilizá-los posteriormente](#Resources)  
  
##  <a name="Brushes"></a> Pincéis: Modificar a aparência de um objeto  
 Aplica um pincel a um objeto, se você quiser alterar sua aparência.  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Pincéis Editor](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### Pintar uma imagem ou padrão em um objeto de repetição  
 Pintar uma imagem ou padrão em um objeto de repetição usando um *pincel lado a lado*.  
  
 Para criar um pincel lado a lado, você começa criando um *Pincel de imagem*, *Pincel de desenho*, ou *Pincel visual* recursos.  
  
 Crie um pincel de imagem usando uma imagem.  As ilustrações a seguir mostram o pincel de imagem, o pincel de imagem lado a lado e o pincel da imagem invertida.  
  
 Crie um pincel de desenho usando um desenho como um caminho ou uma forma de vetor.  As ilustrações a seguir mostram o pincel de desenho, o pincel de desenho lado a lado e o pincel de desenho invertido.  
  
 Crie um pincel visual de um controle como um botão.  As ilustrações a seguir mostram o pincel visual e o visual pincel lado a lado.  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Lado a lado pincéis](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Estilos e modelos: criar uma aparência consistente entre controles  
 Você pode criar a aparência e o comportamento de um controle uma vez e aplicá\-lo a outros controles para que você não precisa mantê\-los individualmente.  
  
 **Você deve usar um estilo?**: se você deseja definir propriedades padrão \(como a cor de um botão\), use uma *estilos*.  Você pode modificar um controle, mesmo depois que você aplicou um estilo a ele.  
  
 **Você deve usar um modelo?**: se você quiser alterar a estrutura de um controle, use um *modelo*.  Imagine a conversão de um gráfico ou um logotipo a um botão.  Você não pode modificar um controle depois que você aplicou um modelo a ela.  
  
### Criar um modelo ou estilo  
 Há duas maneiras de criar um modelo.  Você pode converter qualquer objeto na sua prancheta a um controle ou você pode basear seu modelo em um controle existente.  
  
 Para converter qualquer objeto em um modelo de controle, selecione o objeto e, em seguida, o **ferramentas** menu, escolha **transformar em controle**.  
  
 Se você deseja basear o modelo em um controle existente, selecione um objeto na prancheta.  Em seguida, na parte superior da prancheta, escolha o botão de navegação estrutural, escolha **Editar modelo**, e, em seguida, escolha **Editar uma cópia** ou **criar vazio**.  
  
 Para criar um estilo, selecione o objeto e, em seguida, o **objeto** menu, escolha **Editar estilo**, e, em seguida, escolha **Editar uma cópia** ou **criar vazio**.  
  
-   Escolha **Editar uma cópia** para iniciar com o estilo ou modelo padrão do controle.  
  
-   Escolha **criar vazio** começar do zero.  
  
 O **Editar atual** opção só aparecerá se você editar um estilo ou modelo que você criou.  Ele não aparecerá para um controle que ainda está usando um modelo de sistema padrão.  
  
 No **Criar recurso de estilo** caixa de diálogo, você pode também nomear o estilo ou modelo para que você pode usá\-lo mais tarde ou você pode aplicar o estilo ou modelo para todos os controles desse tipo.  
  
> [!NOTE]
>  Você não pode criar estilos ou modelos para cada tipo de controle.  Se um controle não oferece suporte a eles, o botão estrutural não aparecerá acima da prancheta.  
>   
>  Para retornar ao escopo de edição do documento principal, clique em **retornar escopo para** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b").  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar um estilo](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Criar um modelo de controle no Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### Aplicar um estilo ou modelo a um controle  
 Clique de um objeto no [Objects and Timeline](http://msdn.microsoft.com/pt-br/135a5a5e-ec6d-4f38-8827-60e284cd5f57) painel, escolha **Editar modelo**, e, em seguida, escolha **Aplicar recurso**.  
  
### Restaurar o estilo ou modelo padrão de um controle  
 Selecione o controle e no [propriedades](http://msdn.microsoft.com/pt-br/135a5a5e-ec6d-4f38-8827-60e284cd5f57) painel, localize o **estilos** ou **modelo** propriedade.  Em seguida, clique em **Opções avançadas** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb"), e, em seguida, clique em **Redefinir** no menu de atalho.  
  
##  <a name="Visual"></a> Estados visuais: Alterar a aparência de um controle com base em seu estado  
 Controles podem ter aparências diferentes de visuais com base em interações do usuário.  Por exemplo, você pode fazer com que um botão ficar verde quando um usuário clica nele, ou você pode executar uma animação.  Reduzir ou aumentar o tempo entre estados visuais usando transições.  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Gerenciar o estado dos controles WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Recursos: Criar cores, estilos e modelos e reutilizá\-los posteriormente  
 Você pode converter qualquer coisa em seu projeto para um recurso.  Um recurso é apenas um objeto que possa ser reutilizado em locais diferentes em seu aplicativo.  Por exemplo, criar uma cor de uma vez, torná\-lo um recurso e, em seguida, usar essa cor em vários objetos.  Para alterar a cor de todos os objetos, basta altere o recurso de cor.  
  
 **Assista a um breve vídeo:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Um breve toque em recursos](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## Consulte também  
 [Criando uma interface de usuário usando o Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)