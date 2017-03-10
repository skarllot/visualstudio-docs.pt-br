---
title: "Testando um aplicativo grande com v&#225;rios mapas de interface do usu&#225;rio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de IU codificados, para aplicativos grandes"
  - "testes de IU codificados, vários mapas de IU"
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# Testando um aplicativo grande com v&#225;rios mapas de interface do usu&#225;rio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico fala sobre como usar testes de IU codificados quando você estiver testando um aplicativo grande usando diversos mapas de interface do usuário.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
 Quando você cria um novo teste de IU codificado, a estrutura de testes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera um código de teste em uma classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> por padrão.  Para obter mais informações sobre como gravar testes de IU codificados, consulte [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) e [Anatomia de um teste de IU codificado](../test/anatomy-of-a-coded-ui-test.md).  
  
 O código gerado para o mapa de interface do usuário contém uma classe para cada objeto com o qual há interação.  Para cada método gerado, é gerada uma classe complementar aos parâmetros de método especificamente para o método em questão.  Se houver uma grande quantidade de objetos, páginas, formulários e controles em seu aplicativo, o mapa de interface do usuário pode ficar muito grande.  Além disso, se houver diversas pessoas trabalhando nos testes, o aplicativo fica pesado com um único arquivo grande de mapa de interface do usuário.  
  
 Usando diversos arquivos desse tipo, você pode proporcionar estes benefícios:  
  
-   Cada mapa pode ser associado a um subconjunto lógico do aplicativo.  Isso facilita o gerenciamento das alterações.  
  
-   Cada testador pode trabalhar em uma seção do aplicativo e fazer check\-in do código sem interferir no trabalho de outros testadores em outras seções do aplicativo.  
  
-   É possível dimensionar as adições feitas na interface do usuário do aplicativo a incrementos, com efeito mínimo sobre os testes em outras seções da interface.  
  
## Você precisa de diversos mapas de interface do usuário?  
 Crie diversos mapas em cada uma destas situações:  
  
-   Diversos conjuntos complexos de controles de interface do usuário compostos que, juntos, executam uma operação lógica, como uma página de registro de um site ou a página de compras de um carrinho de compras.  
  
-   Um conjunto independente de controles que são acessados por diversos pontos do aplicativo, como um assistente com diversas páginas de operações.  Se cada página de um assistente for muito complexa, você pode criar mapas de interface do usuário para cada página.  
  
## Adicionando diversos mapas de interface do usuário  
  
#### Para adicionar um mapa de interface do usuário ao seu projeto de teste de IU codificado  
  
1.  No **Gerenciador de Soluções**, para criar uma pasta em seu projeto de teste de IU codificado que armazene todos os mapas de interface do usuário, clique com o botão direito do mouse no arquivo do projeto de teste de IU, aponte para **Adicionar** e clique em **Nova Pasta**.  Por exemplo, você pode atribuir o nome `UIMaps`.  
  
     A nova pasta é exibida no projeto de teste de IU codificado.  
  
2.  Clique com o botão direito do mouse na pasta `UIMaps`, aponte para **Adicionar** e clique em **Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
    > [!NOTE]
    >  Você deve estar em um projeto de teste de IU codificado para adicionar um novo mapa de testes de IU codificado.  
  
3.  Selecione **Mapa de Teste de IU Codificado** na lista.  
  
     Na caixa **Nome**, insira o nome de um novo mapa de interface do usuário.  Use o nome do componente ou da página que o mapa representará, por exemplo, `HomePageMap`.  
  
4.  Escolha **Adicionar**.  
  
     A janela do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é minimizada e a caixa de diálogo **Construtor de Teste de IU Codificado** aparece.  
  
5.  Registre as ações para o primeiro método e escolha **Gerar Código**.  
  
6.  Depois de registrar todas as ações e asserções do primeiro componente ou da página e agrupá\-las em métodos, feche a caixa de diálogo **Construtor de Teste de IU Codificado**.  
  
7.  Continue a criar mapas de interface do usuário.  Registre as ações e asserções, agrupe\-as em métodos para cada componente e gere o código.  
  
 Em muitos casos, a janela principal do seu aplicativo é uma constante para assistentes, formulários e páginas.  Embora cada mapa de interface do usuário tenha uma classe para a janela principal, provavelmente, todos os mapas fazem referência à mesma janela principal na qual todos os componentes do aplicativo são executados.  Os testes de IU codificados procuram controles hierarquicamente, de cima para baixo, começando na janela principal. Assim, em aplicativos complexos, é possível duplicar a janela principal em todos os mapas de interface do usuário.  Se a janela principal real for duplicada, essa janela sofrerá alterações com diversas modificações.  Isso pode resultar em problemas de desempenho quando você alterna entre os mapas de interface do usuário.  
  
 Para minimizar esse efeito, você pode usar o método `CopyFrom()` para garantir que a nova janela principal do mapa seja a mesma janela principal.  
  
## Exemplo  
 O exemplo a seguir faz parte de uma classe de utilitários que proporciona acesso a cada componente e seus controles filhos, que são representados pelas classes geradas nos diversos mapas de interface do usuário.  
  
 Nesse exemplo, o aplicativo Web `Contoso` tem uma Home page, uma Página de produtos e uma Página de carrinho de compras.  Essas páginas usam a mesma janela principal, que é a janela do navegador.  Há um mapa de interface do usuário para cada página e o código da classe do utilitário é parecido com este:  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Anatomia de um teste de IU codificado](../test/anatomy-of-a-coded-ui-test.md)