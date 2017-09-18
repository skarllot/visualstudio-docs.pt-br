---
title: "Passo a passo: Criando um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: 19
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
ms.openlocfilehash: f2024601b99191b3aafa61be72c2ee7fbba195b7
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Passo a passo: Criando um serviço de linguagem herdado
Usando as classes de linguagem do framework (MPF) de pacote gerenciado para implementar um serviço de linguagem no [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] é simples. Você precisa de um VSPackage para hospedar o serviço de linguagem, o serviço de linguagem e um analisador para seu idioma.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do Visual Studio pacote podem ser encontrado em três locais de modelo diferente no **novo projeto** caixa de diálogo:  
  
1.  Em extensibilidade do Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2.  Sob c# extensibilidade. O idioma padrão do projeto é c#.  
  
3.  Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C++.  
  
### <a name="create-a-vspackage"></a>Crie um VSPackage  
  
1.  Crie um novo VSPackage com o modelo de projeto do Visual Studio Package.  
  
     Se você estiver adicionando um serviço de linguagem a um VSPackage existente, ignore as etapas a seguir e ir diretamente para o procedimento "Criar a classe de serviço de idioma".  
  
2.  Digite MyLanguagePackage para o nome do projeto e clique em **Okey**.  
  
     Você pode usar qualquer nome desejado. Esses procedimentos detalhados aqui supõem MyLanguagePackage como o nome.  
  
3.  Selecione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como a linguagem e a opção para gerar um novo arquivo de chave. Clique em **Avançar**.  
  
4.  Insira as informações da empresa e o pacote apropriadas. Clique em **Avançar**.  
  
5.  Selecione **o comando de Menu**. Clique em **Avançar**.  
  
     Se você não pretende oferecer suporte a trechos de código, basta clicar em Concluir e ignore a próxima etapa.  
  
6.  Digite **Inserir trecho** como o **nome do comando** e `cmdidInsertSnippet` para o **ID do comando**. Clique em **Finalizar**.  
  
     O **nome do comando** e **ID de comando** pode ser tudo o que você deseja, esses são apenas exemplos.  
  
### <a name="create-the-language-service-class"></a>Criar a classe de serviço de linguagem  
  
1.  Em **Solution Explorer**, com o botão direito no projeto MyLanguagePackage, escolha **adicionar**, **referência**e, em seguida, escolha o **adicionar nova referência** botão.  
  
2.  No **adicionar referência** caixa de diálogo, selecione **Microsoft.VisualStudio.Package.LanguageService** no **.NET** guia e clique em **Okey**.  
  
     Isso precisa ser feito apenas uma vez para o projeto de pacote de idioma.  
  
3.  Em **Solution Explorer**, com o botão direito no projeto VSPackage e selecione **adicionar**, **classe**.  
  
4.  Certifique-se de **classe** está selecionado na lista de modelos.  
  
5.  Digite **MyLanguageService.cs** para o nome do arquivo de classe e clique em **adicionar**.  
  
     Você pode usar qualquer nome desejado. Suponha que esses procedimentos detalhados aqui `MyLanguageService` como o nome.  
  
6.  No arquivo MyLanguageService.cs, adicione o seguinte `using` instruções.  
  
     [!code-cs[CreatingALanguageService (ManagedPackageFramework)&1;](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs) ] 
     [!code-vb [CreatingALanguageService (ManagedPackageFramework) n º&1;](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificar o `MyLanguageService` classe derivar o <xref:Microsoft.VisualStudio.Package.LanguageService>classe:</xref:Microsoft.VisualStudio.Package.LanguageService>  
  
     [!code-cs[N º&2; (ManagedPackageFramework) CreatingALanguageService](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs) ] 
     [!code-vb [CreatingALanguageService (ManagedPackageFramework) n º&2;](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Posicione o cursor em "LanguageService" e a partir de **editar**, **IntelliSense** menu, selecione **implementar classe abstrata**. Isso adiciona os métodos mínimos necessários para implementar uma classe de serviço de linguagem.  
  
9. Implementar os métodos abstratos, conforme descrito em [implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrar o serviço de linguagem  
  
1.  Abra o arquivo MyLanguagePackagePackage.cs e adicione o seguinte `using` instruções:  
  
     [!code-vb[CreatingALanguageService (ManagedPackageFramework)&3;](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb) ] 
     [!code-cs [CreatingALanguageService (ManagedPackageFramework)&3;](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrar sua classe de serviço de linguagem, conforme descrito em [registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md). Isso inclui os atributos de ProvideXX e seções de "Proffering o serviço de idioma". Use MyLanguageService onde este tópico usa TestLanguageService.  
  
### <a name="the-parser-and-scanner"></a>O analisador e o Scanner  
  
1.  Implementar um analisador e o scanner para seu idioma, conforme descrito em [analisador de serviço de linguagem herdado e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Como você implementa o analisador e o scanner é integralmente com você e está além do escopo deste tópico.  
  
## <a name="language-service-features"></a>Recursos do serviço de linguagem  
 Para implementar cada recurso no serviço de linguagem, você normalmente deriva uma classe da classe de serviço de idioma apropriado MPF, implementa quaisquer métodos abstratos conforme necessário e substituir os métodos apropriados. Quais classes que você cria e/ou deriva é depende dos recursos que você pretende oferecer suporte. Esses recursos são discutidos em detalhes em [recursos de serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md). O procedimento a seguir é a abordagem geral derivando uma classe de classes MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Derivando uma classe MPF  
  
1.  Em **Solution Explorer**, com o botão direito no projeto VSPackage e selecione **adicionar**, **classe**.  
  
2.  Certifique-se de **classe** está selecionado na lista de modelos.  
  
     Insira um nome para o arquivo de classe adequado e clique em **adicionar**.  
  
3.  No novo arquivo de classe, adicione o seguinte `using` instruções.  
  
     [!code-cs[N º&4; (ManagedPackageFramework) CreatingALanguageService](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs) ] 
     [!code-vb [CreatingALanguageService (ManagedPackageFramework) n º&4;](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modificar a classe para derivar da classe MPF desejado.  
  
5.  Adicione um construtor de classe que usa pelo menos os mesmos parâmetros do construtor da classe base e passar os parâmetros do construtor para o construtor da classe base.  
  
     Por exemplo, o construtor para uma classe deriva de <xref:Microsoft.VisualStudio.Package.Source>classe pode parecer com o seguinte:</xref:Microsoft.VisualStudio.Package.Source>  
  
     [!code-cs[CreatingALanguageService (ManagedPackageFramework)&5;](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs) ] 
     [!code-vb [CreatingALanguageService (ManagedPackageFramework) n º&5;](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Do **editar**, **IntelliSense** menu, selecione **implementar classe abstrata** se a classe base tiver quaisquer métodos abstratos que devem ser implementados.  
  
7.  Caso contrário, posicione o cursor dentro da classe e insira o método a ser substituído.  
  
     Por exemplo, digite `public override` para ver uma lista de todos os métodos que podem ser substituídos na classe.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
