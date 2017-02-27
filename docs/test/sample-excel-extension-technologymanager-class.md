---
title: "Extensão de exemplo do Excel: classe TechnologyManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: mlearned
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6ef83b910860e0a790abbe61e5e844c0adf61d53

---
# <a name="sample-excel-extension-technologymanager-class"></a>Extensão de exemplo do Excel: classe TechnologyManager
Essa classe estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> e é responsável por fornecer os serviços principais para a extensão [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]. Embora a classe base tenha muitos métodos, apenas um subconjunto deles é usado neste exemplo.  
  
 Alguns métodos simplesmente retornam um valor da propriedade. Muitos dos métodos destinam-se a permitir que o desenvolvedor substitua o build de algoritmos padrão para o mecanismo de teste de IU codificado. Esses métodos geram um <xref:System.NotSupportedException> ou retornam `null`, que diz à estrutura para usar o algoritmo padrão.  
  
 Dependendo da complexidade da tecnologia subjacente, desenvolver o código do Gerenciador de tecnologia pode levar de poucas semanas a alguns meses. O Excel fornece uma oportunidade para criar um gerenciador de tecnologia potencialmente muito extenso. Este exemplo é intencionalmente limitado a células e planilhas do Excel e usa formatação limitada.  
  
 Quando for possível, o código do gerenciador de tecnologia usa o canal de comunicação remota do .NET aberto pela classe `Communicator` para extrair informações do suplemento em execução no processo do Excel.  
  
## <a name="com-visibility"></a>Visibilidade COM  
 Observe que essa classe e cada uma das classes de elemento que estendem a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> todas têm o <xref:System.Runtime.InteropServices.ComVisibleAttribute> com um valor de `true` para assegurar que as classes sejam visíveis para COM.  
  
## <a name="technologyname-property"></a>Propriedade TechnologyName  
 Essa substituição da propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> deve fornecer um nome exclusivo e significativo que identifica a tecnologia subjacente para todos os outros componentes da extensão. Para essa extensão, o valor é "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>Método GetControlSupportLevel  
 Essa substituição do método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> retorna um número que indica o nível de suporte que o gerente de tecnologia pode oferecer para o controle representado pelo identificador fornecido. Quanto maior o valor retornado, mais o gerenciador de tecnologia pode dar suporte ao controle. Nesse caso, o método verificará a janela que contém o controle e, se ele for uma planilha do Excel, o método retornará o valor mais alto; caso contrário, ele retornará zero, o que indicará que nenhum suporte é fornecido.  
  
## <a name="methods-to-get-an-element"></a>Métodos para obter um elemento  
 Há vários métodos importantes que são usados pela estrutura de teste de IU codificado para obter um elemento específico da tecnologia, fornecendo um identificador, um ponto na tela ou um elemento de uma tecnologia diferente. O código para esses métodos é auto-explicativo. Os métodos básicos são os seguintes:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>Método ParseQueryId  
 Quando um teste de IU codificado é criado, o usuário pode especificar valores de propriedade para alguns ou todos os controles no teste. Esses valores de propriedade são usados pela estrutura de teste para criar pares de nome-valor chamados propriedades de pesquisa que são usadas para localizar controles específicos de interface do usuário durante o teste. Todas as propriedades de pesquisa juntas representam o valor da propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> de cada elemento na tecnologia, o que inclui todos os controles. Como um controle pode ser encontrado várias vezes durante um teste, esse método permite que o gerente de tecnologia otimize a análise das propriedades de pesquisa para o controle fornecido. Esse método também retorna um cookie que a estrutura pode utilizar para pesquisas subsequentes para o controle. Essa implementação do método usa o método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> para analisar as propriedades de pesquisa.  
  
## <a name="matchelement-method"></a>Método MatchElement  
 Para executar uma pesquisa de controle pelo gerenciador de tecnologia, você pode implementar o método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> para retornar uma matriz de possíveis correspondências ou gerar <xref:System.NotSupportedException>, que informa a estrutura para usar seu próprio algoritmo de pesquisa. De qualquer forma, você deve implementar o método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>, em que essa implementação usa novamente o método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="navigation-methods"></a>Métodos de navegação  
 Esses métodos obtêm o pai, filhos ou irmãos do elemento fornecido da hierarquia de interface do usuário. O código é simples e claramente comentado.  
  
## <a name="getexcelelement-internal-method"></a>Método interno GetExcelElement  
 Esse método interno usa um identificador de janela e informações sobre um elemento do Excel e retorna o elemento do Excel solicitado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)


<!--HONumber=Feb17_HO4-->


