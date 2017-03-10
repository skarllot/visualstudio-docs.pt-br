---
title: "Passo a passo: Estendendo VSPackages gerenciados atrav&#233;s da automa&#231;&#227;o | Microsoft Docs"
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
  - "VSPackages gerenciados, estendendo usando a automação"
  - "automação [Visual Studio SDK], instruções passo a passo"
  - "automação [Visual Studio SDK] VSPackages gerenciados"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# Passo a passo: Estendendo VSPackages gerenciados atrav&#233;s da automa&#231;&#227;o
Este passo a passo ilustra como usar a automação para criar um VSPackage gerenciado que manipula o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\). Criar um exemplo gerenciado VSPackage e, em seguida, usar os métodos de automação em VSPackage resultante para exibir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Propriedades de **saída** janela.  
  
## Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do pacote do Visual Studio pode ser encontrado em três locais diferentes de **novo projeto** caixa de diálogo:  
  
1.  Em extensibilidade do Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2.  Sob c\# extensibilidade. O idioma padrão do projeto é c\#.  
  
3.  Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C\+\+.  
  
### Para criar um VSPackage gerenciado  
  
1.  Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] empacotar projeto chamado `Auto`.  
  
     Para obter mais informações sobre como criar um VSPackage gerenciado, consulte [Passo a passo: Criando um comando de Menu usando o modelo de pacote do Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Sobre o **Select a Programming Language** página, defina o idioma para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
3.  Mantenha os valores padrão **informações básicas sobre o VSPackage** página.  
  
4.  Sobre o **Selecionar opções VSPackage** selecione o **comando de Menu** caixa de seleção.  
  
5.  Sobre o **Opções de comando** página, altere o **nome do comando** para `Auto`.  
  
6.  Clique o **Concluir** botão.  
  
     O modelo gera um projeto gerenciado chamado automaticamente.  
  
7.  Crie a solução e verifique se ele é compilado sem erros.  
  
### Para chamar o modelo de automação  
  
1.  Em **Solution Explorer**, com o botão direito no nó do projeto automaticamente e, em seguida, clique em **Add**, **referência**.  
  
2.  Sobre o **.NET** guia do **referência** caixa de diálogo, clique duas vezes em **EnvDTE**.  
  
     Isso adiciona uma referência ao namespace EnvDTE automação.  
  
3.  No arquivo AutoPackage, adicione a seguinte referência de namespace.  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  No arquivo AutoPackage, substitua o corpo do `MenuItemCallback` método com as seguintes linhas:  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 Esse código chama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obter uma <xref:EnvDTE.DTE> objeto automation que representa o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. O código de automação em `MenuItemCallback` cria um novo painel no **saída** janela chamada **teste**. O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nome e versão são gravados para o novo **saída** painel.  
  
1.  Criar e iniciar o projeto automaticamente no modo de depuração pressionando F5.  
  
     Isso inicia o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compilação experimental \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\).  
  
    > [!NOTE]
    >  Ambas as versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estão abertos neste momento.  
  
2.  No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp diante o **ferramentas** menu, clique em **automático**.  
  
     Um novo painel chamado **teste** abre no **saída** janela e exibe o seguinte:  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     Em que x. xx é o mais recente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] número de versão.  
  
     Para obter mais informações sobre exemplos de automação, consulte [exemplos de automação para Visual Studio](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en).  
  
## Consulte também  
 [Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)