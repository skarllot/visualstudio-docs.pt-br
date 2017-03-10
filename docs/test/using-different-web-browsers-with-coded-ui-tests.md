---
title: "Usando navegadores diferentes com testes de interface do usu&#225;rio codificada | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "mlearned"
manager: "douge"
---
# Usando navegadores diferentes com testes de interface do usu&#225;rio codificada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os testes de IU codificados podem automatizar testes para aplicativos Web gravando os testes usando o Internet Explorer.  Você pode personalizar o teste e executá\-lo usando o Internet Explorer ou outros tipos de navegador para esses aplicativos Web.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
-   Sistemas operacionais:  
  
    -   Microsoft Windows 7  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Versões de navegadores da Web:  
  
    -   Windows Internet Explorer 9  
  
    -   Windows Internet Explorer 10  
  
    -   Para as versões suportadas do Mozilla Firefox e Google Chrome, acesse [aqui](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
-   Instale os [Componentes Selenium para Testes de IU Codificados entre Navegadores](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **O que tem suporte por todos os navegadores da Web?**  
  
-   [Adicionar código personalizado para controlar recursos](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) como propriedades, pesquisa e waiters de reprodução.  
  
-   Pop\-ups e caixas de diálogo  
  
-   [Executar JavaScript básico sem tipo de retorno](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Pesquisar resiliência \(usando correspondência inteligente\) e [melhorias de desempenho](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## Por que eu deveria usar testes de IU codificados em vários tipos de navegadores da Web?  
 Testando seu aplicativo Web com uma variedade de tipos de navegadores da Web, você emula melhor a experiência de IU de seus usuários que podem usar navegadores diferentes.  Por exemplo, o aplicativo pode incluir um controle ou um código no Internet Explorer que não seja compatível com outros navegadores da Web.  Executando os testes de IU codificados em outros navegadores, você pode identificar e corrigir qualquer problema antes que isso afete seus clientes.  
  
## Como faço para gravar e reproduzir testes de IU codificados em aplicativos Web usando os navegadores da Web com suporte?  
 **Gravação:** você deve usar o Construtor de Teste de IU Codificado para registrar o teste do aplicativo Web usando o Internet Explorer.  Opcionalmente, você pode adicionar validação e código personalizado para os controles testados usando um conjunto predefinido de propriedades como você faria normalmente para testes de IU codificados.  Para obter mais informações, consulte [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Você não pode gravar testes de IU codificados usando os navegadores Google Chrome ou Mozilla Firefox.  
  
 **Reprodução com o Internet Explorer:** quando nenhum navegador é especificado explicitamente, o teste executará no Internet Explorer por padrão.  Você pode declarar explicitamente o navegador a ser usado definindo a propriedade **BrowserWindow.CurrentBrowser** no código de teste.  Para o Internet Explorer, essa propriedade deve ser definida como **IE** ou **Internet Explorer**.  
  
 **Reprodução com navegadores da Web diferentes do Internet Explorer:** para reproduzir em navegadores da Web diferentes do Internet Explorer, altere a propriedade BrowserWindow.CurrentBrowser no código de teste para **Firefox** ou **Chrome**.  
  
 Para reproduzir testes em navegadores da Web que não sejam o IE, você deve instalar o **Selenium components for Coded UI Cross Browser Testing**.  
  
#### Instalando componentes Selenium  
  
1.  No menu **Ferramentas**, escolha **Extensões e Atualizações**.  
  
2.  Na caixa de diálogo Extensão e Atualizações, procure por `Componentes Selenium para testes entre navegadores`.  
  
3.  Realce a extensão e escolha **Baixar**.  
  
    > [!TIP]
    >  Também é possível baixar os componentes Selenium para Testes de IU Codificados entre Navegadores [aqui](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 Para obter mais informações sobre a criação e o uso de testes de IU codificados, consulte [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### Habilitar depuração  
 Para habilitar a depuração em seu aplicativo Web, conclua as seguintes opções de configuração:  
  
1.  Habilitar Apenas Meu Código:  
  
    1.  No menu **Ferramentas**, escolha**Opções** e **Depuração**.  
  
    2.  Selecione **Habilitar Apenas Meu Código**.  
  
2.  Desabilitar exceções CLR:  
  
    1.  No menu **Depurar**, escolha **Exceções**.  
  
    2.  Para **Exceções de Common Language Runtime**, desmarque **Sem tratamento do usuário**.  
  
##  <a name="generate"></a> *Não vejo a opção para alterar BrowserWindow.CurrentBrowser no teste de IU codificado.*  
 Você pode usar uma versão do [!INCLUDE[vs2011_first](../test/includes/vs2011_first_md.md)] que não oferece suporte a testes de IU codificados usando vários navegadores da Web.  Para usar esses testes de UI codificados, você deve usar o Visual Studio Enterprise.  
  
 *O que mais devo saber?*  
 **Observações**  
  
-   ![Pré&#45;requisitos](../test/media/prereq.png "Prereq") O navegador da Web Apple Safari não tem suporte.  
  
-   ![Pré&#45;requisitos](../test/media/prereq.png "Prereq") A ação de iniciar o navegador da Web deve fazer parte de teste de IU codificado.  
  
     Se você tiver um navegador da Web já aberto e quiser executar etapas nele, a reprodução falhará a menos que você esteja usando o Internet Explorer.  Consequentemente, é uma prática recomendada incluir a inicialização do navegador da Web como parte dos testes de IU codificados.  
  
-   ![Pré&#45;requisitos](../test/media/prereq.png "Prereq") Não há suporte para automatizar ações de IU baseadas em navegadores específicos, como maximizar, minimizar e restaurar.  
  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Você pode configurar a saída para incluir capturas de tela nos logs de IU codificados.  Para fazer isso, você precisa definir algumas configurações no arquivo QTAgent32.exe.config.  Por padrão, esse arquivo é instalado no seguinte local:  
  
     **C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Common7\\IDE**  
  
     Defina os seguintes valores:  
  
    -   `EqtTraceLevel` na seção `system.diagnostics`.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         Definindo o valor para 3 ou mais, as captura de tela são tiradas para cada ação.  Quando o valor é definido para 1 ou 2, as capturas de tela são feitas apenas para ações de erro.  
  
     Para obter mais informações, consulte [Analisando testes de interface de usuário codificada usando logs de teste de interface de usuário codificada](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## Recursos externos  
  
### Vídeos  
 [Gravar no IE e reproduzir em qualquer lugar](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!%20183%20&%20authkey%20=!%20Https://SkyDrive.Live.com/redir?RESID=ae5cd7309cccc43c!183&authkey=!anqaltczbtjrimu)  
  
 [criar testes entre navegadores com o construtor de teste de IU codificado](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!%20184%20&%20authkey%20=!%20Https://SkyDrive.Live.com/redir?RESID=ae5cd7309cccc43c!184&authkey=!akg8csow_qmetq8)  
  
 [criar testes entre navegadores usando codificação manual simples sem mapa da IU](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!%20186%20&%20authkey%20=!%20Https://SkyDrive.Live.com/redir?RESID=ae5cd7309cccc43c!186&authkey=!ajaevxjnsefyat4)  
  
 [executar testes entre navegadores sequencialmente em vários navegadores](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!%20187%20&%20authkey%20=!%20Https://SkyDrive.Live.com/redir?RESID=ae5cd7309cccc43c!187&authkey=!adi8ecqkxhnpor8)  
  
 [solucionar falhas de teste de navegador entre](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!%20182%20&%20authkey%20=!%20AEpS48i295B49FI)  
  
### Diretriz  
 [Teste para entrega contínua com o Visual Studio 2012 – capítulo 2: testes de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [teste para entrega contínua com o Visual Studio 2012 – capítulo 5: automatizando testes do sistema](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### Perguntas frequentes  
 [Testes de UI codificados FAQ \- 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [\-2 de perguntas frequentes sobre testes de UI codificados](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### Fórum  
 [Visual Studio automação de testes de IU \(inclui teste de IU\)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## Consulte também  
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analisando testes de interface de usuário codificada usando logs de teste de interface de usuário codificada](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)