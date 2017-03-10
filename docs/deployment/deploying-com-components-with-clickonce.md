---
title: "Implantando componentes do COM com o ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, componentes COM"
  - "componentes COM, implantando"
  - "componentes, implantando"
  - "implantando aplicativos [ClickOnce], componentes COM"
  - "implantação COM sem registro"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implantando componentes do COM com o ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Implantação de componentes do legado COM tradicionalmente tem sido uma tarefa difícil.  Componentes precisam ser registrados globalmente e, portanto, podem causar efeitos colaterais indesejáveis entre aplicativos sobrepostos.  Essa situação geralmente não é um problema no.NET Framework, pois são completamente isolados em um aplicativo de componentes ou são compatíveis com o lado a lado.  Visual Studio permite que você implante componentes isolados do COM no Windows XP ou sistema de operacional superior.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Fornece um mecanismo fácil e seguro para a implantação de seu.NET seguros.  No entanto, se os aplicativos usam componentes legados do COM, você precisará executar etapas adicionais para implantá\-los.  Este tópico descreve como implantar componentes isolados de COM e fazer referência a componentes nativos \(por exemplo, de Visual Basic 6.0 ou Visual C\+\+\).  
  
 Para obter mais informações sobre como implantar os componentes isolados do COM, consulte "Simplifique a implantação de aplicativos com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro" em [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/04\/RegFreeCOM\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).  
  
## COM sem registro  
 COM sem registro é uma nova tecnologia de implantação e ativação componentes isolados do COM.  Ele funciona colocando de biblioteca todas as do componente de tipos e informações de registro que é normalmente instaladas no registro do sistema em um arquivo XML chamado um manifesto, armazenado na mesma pasta que o aplicativo.  
  
 Um componente COM o isolamento requer que ele seja registrado na máquina do desenvolvedor, mas ele não precisa ser registrado no computador do usuário final.  Para isolar um componente COM, tudo o que você precisa fazer é definir sua referência  **isolada** propriedade para  **True**.  Por padrão, essa propriedade é definida como  **False**, indicando que ele deve ser tratado como uma referência de COM registrados.  Se essa propriedade for  **True**, faz com que um manifesto a ser gerado para este componente em tempo de compilação.  Ele também faz com que os arquivos correspondentes a serem copiados para a pasta do aplicativo durante a instalação.  
  
 Quando o gerador de manifesto encontra uma referência de COM isolado, ele enumera todos os `CoClass` definições para todas as classes COM o arquivo de biblioteca de tipo de entradas na biblioteca de tipos do componente, a correspondência de cada entrada com seus dados de registro correspondentes e geração de manifestam.  
  
## Implantação de componentes COM sem registro usando ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]tecnologia de implantação é bem adequada para a implantação de componentes COM isolado, pois ambos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM sem registro exigem que um componente tem um manifesto para ser implantado.  
  
 Normalmente, o autor do componente deve fornecer um manifesto.  Caso contrário, no entanto, o Visual Studio é capaz de gerar um manifesto automaticamente para um componente COM.  A geração de manifesto é realizada durante a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publicar processo; Para obter mais informações, consulte [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md).  Esse recurso também permite que você aproveite os componentes legados que você desenvolveu em ambientes de desenvolvimento anteriores como, por exemplo, Visual Basic 6.0.  
  
 Há duas maneiras que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implanta os componentes COM:  
  
-   Usar o bootstrapper para implantar os componentes COM. Isso funciona em todas as plataformas com suporte.  
  
-   Use a implantação de isolamento \(também conhecido como COM sem registro\) do componente nativo.  No entanto, isso só funcionará em um sistema de operacional superior ou o Windows XP.  
  
### Exemplo de isolar e implantando um componente simples  
 Para demonstrar a implantação de componente COM sem registro, este exemplo cria um aplicativo baseado no Windows em Visual Basic que faz referência a um componente COM nativo isolado criado usando o Visual Basic 6.0 e implantá\-lo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Primeiro, você precisará criar o componente nativo COM:  
  
##### Para criar um componente nativo  
  
1.  Usando Visual Basic 6.0, a partir do  **arquivo** menu, clique em  **nova**, em seguida,  **projeto**.  
  
2.  No  **Novo projeto** caixa de diálogo, selecione o  **Visual Basic** nó e selecione um  **ActiveX DLL** project.  No  **nome** , digite  `VB6Hello`.  
  
    > [!NOTE]
    >  Somente tipos de projeto DLL de ActiveX e ActiveX de controle são compatíveis com o COM sem registro; Não há suporte para tipos de projeto EXE de ActiveX e ActiveX de documento.  
  
3.  Em  **Solution Explorer**, clique duas vezes em  **Class1. vb** para abrir o editor de texto.  
  
4.  No Class1. vb, adicione o seguinte código após o código gerado para o `New` método:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Crie o componente.  Do  **Build** menu, clique em  **Build Solution**.  
  
> [!NOTE]
>  COM sem registro oferece suporte somente as DLLs e COM controla os tipos de projeto.  Você não pode usar EXEs com sem registro COM.  
  
 Agora você pode criar um aplicativo baseado no Windows e adicionar uma referência ao componente COM a ele.  
  
##### Para criar um aplicativo baseado no Windows usando um componente COM  
  
1.  Usando a partir de Visual Basic, o  **arquivo** menu, clique em  **novo**, em seguida,  **projeto**.  
  
2.  No  **Novo projeto** caixa de diálogo, selecione o  **Visual Basic** nó e selecione  **Windows Application**.  No  **nome** , digite  `RegFreeComDemo`.  
  
3.  Em  **Solution Explorer**, clique no  **Mostrar todos os arquivos** botão para exibir as referências do projeto.  
  
4.  Com o botão direito do  **referências** nó e selecione  **Add Reference** no menu de contexto.  
  
5.  No  **Add Reference** caixa de diálogo, clique no  **Procurar** , navegue até VB6Hello.dll e selecione a ele.  
  
     A  **VB6Hello** referência aparecerá na lista de referências.  
  
6.  Aponte para o  **caixa de ferramentas**, selecione um  **botão** de controle e arraste\-o para o  **Form1** formulário.  
  
7.  No  **Propriedades** janela, defina o botão  **texto** propriedade para Hello.  
  
8.  Clique duas vezes no botão para adicionar o código de manipulador e no arquivo de código, adicione código para que o manipulador lê como segue:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Execute o aplicativo.  Do  **Debug** menu, clique em  **Start Debugging**.  
  
 Em seguida, você precisará isolar o controle.  Cada componente COM que o aplicativo usa é representado no seu projeto como uma referência de COM.  Essas referências são visíveis a  **referências** nó a  **Solution Explorer** janela.  \(Observe que você pode adicionar referências diretamente usando o  **Add Reference** no  **projeto** menu, ou indiretamente por arrastar um controle ActiveX para seu formulário.\)  
  
 As etapas a seguir mostram como isolar o componente COM e publicar o aplicativo atualizado que contém o controle isolado:  
  
##### Para isolar um componente COM  
  
1.  Em  **Solution Explorer**, no  **referências** nó, selecione o  **VB6Hello** referência.  
  
2.  No  **Propriedades** janela, altere o valor da  **isolada** propriedade a partir de  **False** para  **True**.  
  
3.  Do  **Build** menu, clique em  **Build Solution**.  
  
 Agora, quando você pressionar F5, o aplicativo funcione conforme o esperado, mas ele agora está sendo executado sem registro COM.  Para provar isso, tente remover o componente VB6Hello.dll o registro e executar RegFreeComDemo1.exe fora do IDE Visual Studio.  Desta vez, quando o botão for clicado, ele ainda funciona.  Se você renomear temporariamente o manifesto do aplicativo, ele irá falhar novamente.  
  
> [!NOTE]
>  Você pode simular a ausência de um componente COM, removendo\-o temporariamente.  Abra um prompt de comando, vá para a pasta do sistema digitando  `%windir%\system32 do cd /d`, em seguida, cancelar o registro do componente digitando  `regsvr32 /u VB6Hello.dll`.  Você pode registrá\-lo novamente, digitando  `regsvr32 VB6Hello.dll`.  
  
 A etapa final é publicar o aplicativo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### Para publicar uma atualização do aplicativo com um componente isolado do COM  
  
1.  Do  **Build** menu, clique em  **Publicar RegFreeComDemo**.  
  
     O Assistente de Publicação aparece.  
  
2.  No Publish Wizard, especifique um local no disco do computador local onde você pode acessar e examinar os arquivos publicados.  
  
3.  Clique em  **Concluir** para publicar o aplicativo.  
  
 Se você examinar os arquivos publicados, você notará que o arquivo de Sysmon. ocx está incluído.  O controle é totalmente isolado para este aplicativo, que significa que, se a máquina do usuário final tem outro aplicativo usando uma versão diferente do controle, ele não pode interferir com este aplicativo.  
  
## Referenciando Assemblies nativos  
 Visual Studio oferece suporte a referências a 6.0 nativo de Visual Basic ou assemblies de C\+\+; Essas referências são chamadas de referências nativas.  Você pode dizer se uma referência é nativa, confirmando que seu  **Tipo de arquivo** propriedade estiver definida como  **nativo** ou  **ActiveX**.  
  
 Para adicionar uma referência nativa, use o  **Add Reference** de comando e navegue para o manifesto.  Alguns componentes coloque o manifesto dentro da DLL.  Nesse caso, você pode simplesmente escolher da própria DLL e Visual Studio irá adicioná\-la como uma referência nativa se detectar que o componente contém um manifesto incorporado.  Visual Studio incluirá também automaticamente quaisquer arquivos dependentes ou assemblies listados no manifesto, se eles estiverem na mesma pasta que o componente referenciado.  
  
 Isolamento de controle COM torna fácil de implantar os componentes COM que ainda não tenham manifestos.  Entretanto, se um componente é fornecido com um manifesto, você pode referenciar diretamente o manifesto.  Na verdade, você sempre deve usar o manifesto fornecido pelo autor do componente sempre que possível, em vez de usar o  **isolada** propriedade.  
  
## Limitações de implantação de componente COM sem registro  
 COM sem registro fornece vantagens evidentes em técnicas de implantação tradicional.  No entanto, existem algumas limitações e advertências também devem ser apontadas.  A maior limitação é que ele só funciona no Windows XP ou superior.  A implementação de COM sem registro exigiu alterações à maneira na qual os componentes são carregados no núcleo do sistema operacional.  Infelizmente, não há nenhuma camada de suporte de nível inferior para sem registro COM.  
  
 Não, todos os componentes é um candidato adequado sem registro COM.  Um componente não é um adequado, se qualquer um dos procedimentos a seguir forem verdadeiras:  
  
-   O componente é um servidor fora do processo.  Não há suporte para servidores EXE; somente as DLLs são suportadas.  
  
-   O componente é parte do sistema operacional ou é um componente do sistema, como XML, o Internet Explorer ou o Microsoft Data Access Components \(MDAC\).  Você deve seguir a diretiva de redistribuição do autor do componente; Verifique com o fornecedor.  
  
-   O componente é parte de um aplicativo, como, por exemplo, Microsoft Office.  Por exemplo, você não deve tentar isolar o modelo de objeto do Microsoft Excel.  Isso faz parte do Office e só pode ser usado em um computador com o produto completo do Office instalado.  
  
-   O componente destina\-se ao uso como um add\-in ou um snap\-in, por exemplo um add\-in do Office ou um controle em um navegador da Web.  Tais componentes geralmente requerem algum tipo de esquema de registro definido pelo ambiente de hospedagem que está além do escopo do próprio manifesto.  
  
-   O componente gerencia um dispositivo físico ou virtual para o sistema, por exemplo, um driver de dispositivo para um spooler de impressão.  
  
-   O componente é redistribuível de acesso a dados.  Aplicativos de dados geralmente requerem um separado acesso a dados redistribuível para ser instalado antes de serem executados.  Você não deve tentar isolar os componentes como, por exemplo, o controle de dados do Microsoft ADO, o Microsoft OLE DB ou o Microsoft Data Access Components \(MDAC\).  Em vez disso, se seu aplicativo usa o MDAC ou de SQL Server Express, você deve defini\-los como pré\-requisitos; see [Como instalar pré\-requisitos com um aplicativo ClickOnce](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md).  
  
 Em alguns casos, talvez seja possível para o desenvolvedor do componente refazer o design para sem registro COM.  Se isso não for possível, você pode criar e publicar aplicativos que dependem deles por meio do esquema de registro padrão usando o Bootstrapper.  Para obter mais informações, consulte [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
 Um componente COM só pode ser isolado uma vez por aplicativo.  Por exemplo, é possível isolar o mesmo componente COM de dois diferentes  **Biblioteca de classe** os projetos que fazem parte do mesmo aplicativo.  Isso resultará em um aviso de compilação e o aplicativo irá falhar ao carregar em tempo de execução.  Para evitar esse problema, a Microsoft recomenda que você encapsula componentes COM em uma biblioteca de classe única.  
  
 Há vários cenários nos qual COM o registro é obrigatório na máquina do desenvolvedor, mesmo que a implantação do aplicativo não requer registro.  O `Isolated` propriedade requer que o componente COM ser registrado na máquina do desenvolvedor para gerar automaticamente o manifesto durante a compilação.  Há não há recursos de captura de registro que chamam o auto\-registro durante a compilação.  Além disso, qualquer classe não explicitamente definida na biblioteca de tipos não será refletida no manifesto.  Ao usar um componente COM um manifesto pré\-existentes, como, por exemplo, uma referência nativa, o componente talvez não precise ser registrada no tempo de desenvolvimento.  No entanto, o registro é obrigatório se o componente é um controle de ActiveX e você desejar incluí\-lo no  **caixa de ferramentas** e o Windows Forms designer.  
  
## Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)