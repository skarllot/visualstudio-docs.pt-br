---
title: Usando membros do Microsoft.VisualStudio.TestTools.UnitTesting em testes de unidade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 0488f42c64c3079b671e046055112f8366d2c2bf
ms.lasthandoff: 04/04/2017

---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Usando membros do Microsoft.VisualStudio.TestTools.UnitTesting em testes de unidade
A Estrutura de Teste de Unidade dá suporte a testes de unidade no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Use as classes e membros do namespace Microsoft.VisualStudio.TestPlatform.UnitTestFramework> ao codificar testes de unidade. É possível usá-los ao gravar o teste de unidade do zero ou refinar um teste de unidade gerado do código em teste.  
  
## <a name="groups-of-elements"></a>Grupos de Elementos  
 Para ajudar a fornecer uma visão geral mais clara da Estrutura de Teste de Unidade, esta seção organiza os elementos do namespace UnitTesting em grupos de funcionalidades relacionadas.  
  
> [!NOTE]
>  Os elementos de atributo, cujos nomes terminam com a cadeia de caracteres Attribute, podem ser usados com ou sem a cadeia de caracteres Attribute. Por exemplo, os dois exemplos de código a seguir funcionam de forma idêntica:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Elementos Usados Para Teste Controlado por Dados  
 Use os seguintes elementos para configurar testes de unidade controlados por dados. Para obter mais informações, consulte [Como Criar um Teste de Unidade Controlado por Dados](../test/how-to-create-a-data-driven-unit-test.md) e [Passo a Passo: Usando um Arquivo de Configuração para Definir uma Fonte de Dados](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Atributos Usados para Estabelecer uma Ordem de Chamada  
 Um elemento de código decorado com um dos seguintes atributos é chamado no momento em especificado por você. Para obter mais informações, consulte [Anatomia de um Teste de Unidade](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### <a name="for-assemblies"></a>Para Assemblies  
 AssemblyInitialize e AssemblyCleanup são chamados logo após o assembly ser carregado e logo antes de seu assembly ser descarregado.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Para Classes  
 ClassInitialize e ClassCleanup são chamadas logo após a classe ser carregada e logo antes de sua classe ser descarregada.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Para Métodos de Teste  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributos Usados para Identificar Classes de Teste e Métodos  
 Cada classe de teste deve ter o atributo TestClass e cada método de teste deve ter o atributo TestMethod. Para obter mais informações, consulte [Anatomia de um Teste de Unidade](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Classes Assert e Exceções Relacionadas  
 Testes de unidade podem verificar comportamentos específicos do aplicativo pelo uso de vários tipos de instruções Assert, exceções e atributos. Para obter mais informações, consulte [Usando as Classes Assert](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>A Classe TestContext  
 Os seguintes atributos e os valores atribuídos a eles aparecem na janela Propriedades [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de um método de teste específico. Esses atributos não devem ser acessados por meio do código do teste de unidade. Em vez disso, eles afetam as maneiras pelas quais o teste de unidade é utilizado ou executado, seja por meio do IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou pelo mecanismo de testes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Por exemplo, alguns desses atributos aparecem como colunas nas janelas Gerenciador de Testes e Resultados do Teste, o que significa que é possível usá-las para agrupar e classificar testes e resultados de teste. Um desses atributos é TestPropertyAttribute, que pode ser usado para adicionar metadados arbitrários a testes de unidade. Por exemplo, é possível usá-lo para armazenar o nome de uma passagem de teste coberta pelo teste em questão, por meio da marcação do teste de unidade com `[TestProperty("TestPass", "Accessibility")]`. Como alternativa, você pode usá-lo para armazenar um indicador de que o tipo de teste é: `[TestProperty("TestKind", "Localization")]`. A propriedade criada por você com esse atributo e o valor da propriedade atribuído são exibidos na janela Propriedades [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sob o título **Especificidades do teste**.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Classes de Configuração de Teste  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Atributos Usados para a Geração de Relatórios  
 Os atributos desta seção relacionam o método de teste decorados por eles a entidades na hierarquia do projeto de um projeto de equipe [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Classes Usadas com Acessadores Particulares  
 Conforme descrito em [Usar o Publicize para Criar um Acessador Particular](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), é possível gerar um teste de unidade para um método particular. Essa geração cria uma classe de acessador particular, que instancia um objeto da classe PrivateObject. A classe PrivateObject é uma classe wrapper que usa reflexão como parte do processo do acessador particular. A classe PrivateType é semelhante, mas é usada para chamar métodos estáticos privados em vez de chamar os métodos de instância privada.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType  
  
## <a name="see-also"></a>Consulte também  
 Microsoft.VisualStudio.TestPlatform.UnitTestFramework

