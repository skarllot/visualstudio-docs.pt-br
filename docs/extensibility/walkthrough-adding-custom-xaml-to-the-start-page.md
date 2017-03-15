---
title: "Passo a passo: Adicionando XAML personalizado para a página inicial | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 12
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
ms.openlocfilehash: c19658e44daf96b6db96c503de1b59127b673111
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Passo a passo: Adicionando XAML personalizado para a página inicial
Este passo a passo mostra como criar um Visual Studio iniciar página personalizada que contém um navegador da Web.  
  
## <a name="adding-custom-xaml"></a>Adicionar personalizado XAML  
  
1.  Criar uma página de início, seguindo as instruções em [criando uma página de início personalizado](../extensibility/creating-a-custom-start-page.md).  
  
2.  No arquivo de MainWindow. XAML, localize o \<grade > seção.  
  
3.  Adicionar uma \<TabControl > elemento e um \<TabItem > dentro do \< grade > elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Adicione um segundo \<TabItem >, com um \<botão > elemento que abre um novo projeto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testando a página inicial personalizada  
  
1.  Pressione F5.  
  
     A instância experimental do Visual Studio abre com personalizado Start Page instalado, mas não selecionada.  
  
2.  Na instância experimental do Visual Studio, abra o **/opções de ferramentas / ambiente** página.  
  
3.  Selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione o arquivo. XAML e clique em **Okey**.  
  
4.  Sobre o **exibição** menu, clique em **Start Page**.  
  
5.  Clique o **Bing** guia.  
  
     Você deve ver uma página de web do Bing.  
  
6.  Clique o **MyButton** guia.  
  
     Você deve ver uma **MyProject** botão que abre o **novo projeto** caixa de diálogo.  
  
7.  Feche a instância experimental.  
  
## <a name="applying-the-custom-start-page"></a>Aplicando a página inicial personalizada  
  
#### <a name="to-test-the-custom-start-page"></a>Para testar a página de início personalizado  
  
1.  Em **Ferramentas / opções / ambiente**, selecione **inicialização**. Sobre o **Personalizar página inicial** lista, selecione o arquivo. XAML e clique em **Okey**.  
  
## <a name="next-steps"></a>Próximas etapas  
 A página do Visual Studio iniciar agora contém uma guia que exibe uma guia de MyButton e uma guia do navegador da Web. Você pode criar páginas personalizadas iniciar com outra funcionalidade usando o *de lógica* modelo para adicionar um arquivo. dll personalizado, como mostrado na [adicionando o controle de usuário para a página de início](../extensibility/adding-user-control-to-the-start-page.md). Você pode compartilhar páginas de inicialização personalizada com outros usuários, publicando o arquivo. VSIX resultante para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web ou para outro site da Web ou rede compartilhar. Para obter mais informações, consulte [Implantando páginas de inicialização personalizada](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles de contêiner WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
