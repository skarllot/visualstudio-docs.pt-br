---
title: "Como: criar uma solução de linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Como criar uma solução de linguagem específica do domínio
Uma linguagem específica do domínio (DSL) é criada usando especializado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Antes de iniciar este procedimento, você deve primeiro instalar esses componentes:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|SDK de Visualização e Modelagem do Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Criando uma solução de linguagem específica do domínio  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Para criar uma solução de linguagem específica do domínio  
  
1.  Inicie o assistente DSL.  
  
    1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
    2.  A caixa de diálogo **Novo Projeto** é exibida.  
  
    3.  Em **tipos de projeto**, expanda o **Other Project Types** nó e clique em **extensibilidade**.  
  
    4.  Clique em **Designer de linguagem específica do domínio**.  
  
    5.  No **nome** , digite um nome para a solução. Clique em **OK**.  
  
         O **Assistente de Designer de linguagem específica do domínio** é exibida.  
  
        > [!NOTE]
        >  Preferencialmente, o nome que você digita deve ser um identificador válido do Visual c#, porque ele pode ser usado para gerar código.  
  
     ![Criar caixa de diálogo DSL](~/docs/modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Escolha um modelo DSL.  
  
     Sobre o **selecionar opções de linguagem específica do domínio** página, selecione um dos modelos de solução, como **linguagem mínima**. Escolha um modelo semelhante a DSL que você deseja criar.  
  
     Para obter mais informações sobre modelos de solução, consulte [escolhendo um modelo de solução de linguagem específica do domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Digite uma extensão de nome de arquivo **extensão** página. Ele deve ser exclusivo no seu computador e em qualquer computador no qual você deseja instalar a DSL. Você deve ver a mensagem **nenhum aplicativo ou editores do Visual Studio usam essa extensão**.  
  
    -   Se você usou a extensão de nome de arquivo anteriores DSLs experimentais que não foram totalmente instaladas, você pode limpá-los fora usando o **redefinir a instância Experimental** ferramenta, que pode ser encontrada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu SDK.  
  
    -   Se outro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que usa essa extensão de arquivo foi totalmente instalado no seu computador, considere a desinstalá-lo. Sobre o **ferramentas** menu, clique em **Extension Manager**.  
  
4.  Inspecionar e ajustar se necessário, os campos nas páginas restantes do assistente. Quando estiver satisfeito com as configurações, clique em **concluir**. Para obter mais informações sobre as configurações, consulte [páginas do Assistente de Designer DSL](#settings).  
  
     O assistente cria uma solução que tem dois projetos, que são nomeados **Dsl** e **DslPackage**.  
  
    > [!NOTE]
    >  Se você vir uma mensagem que o alerta não executar modelos de texto de fontes não confiáveis, clique em **Okey**. Você pode definir essa mensagem não seja exibida novamente.  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>As páginas do Assistente de Designer DSL  
 Você pode deixar a vários campos inalterados de seus valores padrão. No entanto, certifique-se de que você definir o campo de extensão de arquivo.  
  
### <a name="solution-settings-page"></a>Página de configurações da solução  
 **Qual o modelo que você deseja basear sua linguagem específica do domínio?**  
 Escolha um modelo semelhante a DSL que você deseja criar. Os diferentes modelos fornecem pontos de partida. Quando você seleciona um modelo de solução, o assistente exibe uma descrição. Para obter mais informações sobre modelos de solução, consulte [escolhendo um modelo de solução de linguagem específica do domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **O que você deseja nomear sua linguagem específica do domínio?**  
 O padrão é o nome da solução. Código é gerado com esse valor. Ele deve ser válido como um nome de classe do c#.  
  
### <a name="file-extension-page"></a>Página de extensão de arquivo  
 **Qual extensão deve modelar arquivos usam?**  
 Digite uma nova extensão de arquivo.  
  
 Verifique se que essa extensão de arquivo não já foi registrado para uso nesse computador, da seguinte maneira:  
  
 Procure **outras ferramentas e aplicativos registrados para lidar com essa extensão**. Se você vir a mensagem **nenhum aplicativo ou editores do Visual Studio usam essa extensão**, você pode usar essa extensão de arquivo.  
  
 Se você vir uma lista de ferramentas ou pacotes, você deve fazer o seguinte:  
  
-   Digite uma extensão de arquivo diferente.  
  
     \- ou -  
  
-   Redefinir o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instância Experimental. Isso cancelará todas as DSLs que você criou anteriormente. Sobre o **iniciar** menu, clique em **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**e, em seguida, **redefinir a instância do Microsoft Visual Studio 2010 Experimental**. Você pode recriar outras DSLs que você deseja usar novamente.  
  
     \- ou -  
  
-   Se um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão que usa essa extensão de arquivo tiver sido completamente instalado no seu computador, desinstalá-lo. Sobre o **ferramentas** menu, clique em **Extension Manager**.  
  
### <a name="product-settings-page"></a>Página de configurações do produto  
 **O que é o nome do produto que pertence a nova linguagem específica do domínio?**  
 O padrão é o nome DSL.  
  
 Esse valor é usado no Windows Explorer (ou Explorador de arquivos) para descrever os arquivos que têm essa extensão de arquivo.  
  
 **O que é o nome da empresa que o produto pertence?**  
 Nome da sua empresa.  
  
 Esse valor é incorporado nas propriedades do pacote DSL AssemblyInfo.  
  
 **O que é o namespace raiz para projetos nesta solução?**  
 O padrão é um nome composto de sua empresa e nomes de produtos.  
  
### <a name="signing-page"></a>Página Assinatura  
 **Criar um arquivo de chave de nome forte**  
 A opção padrão é criar uma nova chave para assinar o seu assembly DSL.  
  
 **Use a chave de nome forte existente**  
 Use esta opção se você deseja integrar a DSL com outro assembly.  
  
 Para obter mais informações sobre nomes fortes, consulte [Creating and Using Strong-Named Assemblies](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Consulte também  
 [Como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

