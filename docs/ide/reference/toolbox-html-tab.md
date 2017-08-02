---
title: Caixa de ferramentas, Guia HTML | Microsoft Docs
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: bc243e4d5ec1141244314109aa76fef86287d1c1
ms.contentlocale: pt-br
ms.lasthandoff: 06/23/2017

---
# <a name="toolbox-html-tab"></a>Caixa de Ferramentas, Guia HTML
A guia **HTML** da Caixa de ferramentas fornece componentes que são úteis em páginas e formulários da Web. Para exibir essa guia, primeiro abra um documento para edição no designer de HTML. No menu **Exibir**, clique em **Caixa de ferramentas** e, em seguida, na guia **HTML** da Caixa de ferramentas.  

 Para criar uma instância de uma ferramenta na guia **HTML**, clique duas vezes na ferramenta para adicioná-la ao documento no ponto de inserção atual ou selecione a ferramenta e arraste-a para a posição desejada na superfície de edição.  

## <a name="tasks"></a>Tarefas  

-   [Usando a caixa de ferramentas](../../ide/using-the-toolbox.md)  

## <a name="ui-elements"></a>Elementos da interface do usuário  
 As ferramentas a seguir estão disponíveis por padrão na guia HTML.  

 **Ponteiro**  
 ![Ponteiro de página HTML do Designer de Dispositivo Móvel do ASP.NET](~/docs/ide/reference/media/vxpointer.gif "vxPointer")  

 Essa ferramenta é selecionada por padrão quando uma guia da Caixa de ferramentas é aberta. Não pode ser excluído. O ponteiro permite arrastar objetos para a superfície do modo de exibição de Design, redimensioná-los e reposicioná-los na página ou no formulário. Para obter mais informações, consulte [Usando a caixa de ferramentas](../../ide/using-the-toolbox.md).  

 **Entrada (Botão)**  
 ![Botão da página da Web HTML](~/docs/ide/reference/media/vxbutton.gif "vxButton")  

 Insere um elemento `input` igual a `type="button"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Button1"` é inserido para o primeiro botão, `id="Button2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Botão)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  

 **Entrada (Redefinição)**  
 ![Captura de tela de HTMLpageResetButton](~/docs/ide/reference/media/vxreset.gif "vxReset")  

 Insere um elemento `input` igual a `type="reset"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Reset1"` é inserido para o primeiro botão de redefinição, `id="Reset2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Redefinição)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  

 **Entrada (Enviar)**  
 ![Captura de tela de HTMLpageToolbarSubmitButton](~/docs/ide/reference/media/vxsubmit.gif "vxSubmit")  

 Insere um elemento `input` igual a `type="submit"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Submit1"` é inserido para o primeiro botão de envio, `id="Submit2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Envio)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  

 **Entrada (Texto)**  
 ![Captura de tela de HTMLpageToolbarTextField](~/docs/ide/reference/media/vxtextfield.gif "vxTextfield")  

 Insere um elemento `input` igual a `type="text"` no documento. Para alterar o texto padrão exibido, edite o atributo `value`. Por padrão, `id="Text1"` é inserido para o primeiro campo de texto, `id="Text2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Texto)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  

> [!IMPORTANT]
>  É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Validando a entrada do usuário em Páginas da Web do ASP.NET (Razor)).  

 **Entrada (Arquivo)**  
 ![Campo de arquivo de paginação HTML](~/docs/ide/reference/media/vxfilefield.gif "vxFilefield")  

 Insere um elemento `input` igual a `type="file"` no documento. Por padrão, `id="File1"` é inserido para o primeiro campo de arquivo, `id="File2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Arquivo)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="File1" type="file" name="File1">  
```  

> [!IMPORTANT]
>  É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Validando a entrada do usuário em Páginas da Web do ASP.NET (Razor)).  

 **Entrada (Senha)**  
 ![Campo de senha do Visual Studio](~/docs/ide/reference/media/vxpassword.gif "vxPassword")  

 Insere um elemento `input` igual a `type="password"`. Por padrão, `id="Password1"` é inserido para o primeiro campo de senha, `id="Password2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Senha)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Password1" type="password" name="Password1">  
```  

> [!IMPORTANT]
>  Se o aplicativo transmitir nomes de usuário e senhas, será necessário configurar o site para usar o protocolo SSL para criptografar a transmissão. Para obter mais informações, consulte “Protegendo conexões com o protocolo SSL” no [Guia de Operações do IIS](http://go.microsoft.com/fwlink/?linkid=47856). Além disso, é recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Validando a entrada do usuário em Páginas da Web do ASP.NET (Razor)).  

 **Entrada (caixa de seleção)**  
 ![Opção Caixa de seleção da caixa de ferramentas da página da Web HTML](~/docs/ide/reference/media/vxcheckbox.gif "vxCheckbox")  

 Insere um elemento `input` igual a `type="checkbox"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Checkbox1"` é inserido para a primeira caixa de seleção, `id="Checkbox2"` para a segunda e assim por diante.  

 Ao arrastar **Entrada (Caixa de seleção)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  

 **Entrada (Opção)**  
 ![Captura de tela de VisualStudioHTMLpageRadioButton](~/docs/ide/reference/media/vxradio.gif "vxRadio")  

 Insere um elemento `input` igual a `type="radio"`. Para alterar o texto exibido, edite a propriedade `name`. Por padrão, `id="Radio1"` é inserido para o primeiro botão de opção, `id="Radio2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Botão de opção)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Radio1" type="radio" name="Radio1">  
```  

 **Entrada (Oculta)**  
 ![Item Oculto da página HTML](~/docs/ide/reference/media/vxhidden.gif "vxhidden")  

 Insere um elemento `input` igual a `type="hidden"`. Por padrão, `id="Hidden1"` é inserido para o primeiro campo oculto, `id="Hidden2"` para o segundo e assim por diante.  

 Ao arrastar **Entrada (Oculta)** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  

 **Área de texto**  
 ![Área de texto da barra de ferramentas da página HTML](~/docs/ide/reference/media/vxtextarea.gif "vxTextarea")  

 Insere um elemento `textarea`. É possível redimensionar a área de texto ou usar as barras de rolagem para exibir o texto que se estende além da área de exibição. Para alterar o texto padrão exibido, edite o atributo `value`. Por padrão, `id="textarea1"` é inserido para a primeira área de texto, `id=" textarea 2"` para a segunda e assim por diante.  

 Ao arrastar **Área de texto** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  

> [!IMPORTANT]
>  É recomendável validar todas as entradas do usuário. Para obter mais informações, consulte [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites) (Validando a entrada do usuário em Páginas da Web do ASP.NET (Razor)).  

 **Tabela**  
 ![Captura de tela de HTMLpageToolbarTable](~/docs/ide/reference/media/vxtable.gif "vxTable")  

 Insere um elemento `table`.  

 Ao arrastar **Tabela** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  

**Image**  
 ![Item Imagem da página HTML](~/docs/ide/reference/media/vximage.gif "vxImage")  

 Insere um elemento `img`. Edite esse elemento para especificar seu `src` e seu texto `alt`.  

 Ao arrastar **Imagem** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<img alt="" src="">  
```  

 **Selecionar**  
 ![Lista suspensa da caixa de ferramentas da página HTML](~/docs/ide/reference/media/vxdropdown.gif "vxDropdown")  

 Insere um elemento `select` suspenso (sem um atributo `size`). Por padrão, `id="select1"` é inserido para a primeira caixa de listagem, `id="select2"` para a segunda e assim por diante.  

 Ao arrastar **Selecionar** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<select id="select1" name="select1"><option selected></option></select>  
```  

 É possível criar um elemento `select` multilinha aumentando o valor da propriedade de tamanho.  

 **Régua horizontal**  
 ![Item Regra Horizontal da página HTML](~/docs/ide/reference/media/vxhorizontal.gif "vxHorizontal")  

 Insere um elemento `hr`. Para aumentar a espessura da linha, edite o atributo `size`.  

 Ao arrastar **Régua Horizontal** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<hr width="100%" size=1>   
```  

 **Div**  
 ![Rótulo da página HTML](~/docs/ide/reference/media/vxlabel.gif "vxLabel")  

 Insere um elemento `div` inclui um atributo `ms_positioning="FlowLayout"`. Com exceção da largura e da altura, esse item é idêntico a um Painel de Layout de Fluxo. Para formatar o texto contido em um elemento `div`, adicione um atributo `class="stylename"` à marcação de abertura.  

 Ao arrastar **Div** para a superfície do modo de exibição de Design, uma marcação HTML como a seguinte é inserida no documento:  

```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  

## <a name="see-also"></a>Consulte também  
 [Caixa de ferramentas](../../ide/reference/toolbox.md)   
 [Usando a caixa de ferramentas](../../ide/using-the-toolbox.md)   

