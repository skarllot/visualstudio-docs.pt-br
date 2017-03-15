---
title: "Visão geral das opções de configuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 10
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
ms.openlocfilehash: 2c188af385d75fed49f6e9aca6703365c3b63ca5
ms.lasthandoff: 02/22/2017

---
# <a name="configuration-options-overview"></a>Visão geral das opções de configuração
Projetos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode oferecer suporte a várias configurações que podem ser criadas, implantados, execução e depurado. Uma configuração é descrito com um conjunto nomeado de propriedades, normalmente os comutadores de compilador e locais de arquivos de um tipo de compilação. Por padrão, novas soluções contêm duas configurações Debug e Release. Essas configurações podem ser aplicadas usando as configurações padrão ou modificado para atender às suas necessidades específicas de solução e/ou projeto. Alguns pacotes podem ser criados de duas maneiras: como um editor de ActiveX ou como um componente no local. Projetos não é necessário dar suporte a várias configurações, no entanto. Se houver apenas uma configuração, essa configuração é mapeada em todas as configurações de solução.  
  
 Configurações normalmente consistem em duas partes — o nome da configuração (por exemplo, Debug ou Release) e as configurações da plataforma. Nome da configuração da plataforma identifica o ambiente que definir os destinos de configuração, como uma API ou plataforma de sistema operacional. Os usuários do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não é possível criar uma plataforma; eles devem escolher dentre as opções um projeto de VSPackage permite. Quando um usuário instala um VSPackage, a plataforma de distribuição criada durante o desenvolvimento do pacote pode ter superfície em qualquer nome desejado da plataforma com base em qualquer critério definido pelo criador do pacote. O usuário pode selecionar na lista de plataformas disponibilizados por meio de VSPackage quando as páginas de propriedades são instanciadas.  
  
 Nomes de plataforma são opcionais, pois nem todos os projetos oferece suporte ao conceito de plataformas. Quando uma configuração não possui um nome de plataforma, a cadeia de caracteres "n/a" é exibido na interface do usuário.  
  
 Cada solução tem seu próprio conjunto de configurações, somente uma delas pode estar ativa por vez. Uma configuração de solução é um conjunto de não mais de uma configuração de cada projeto. "Não mais do que" requisito é devido a opção para excluir um projeto de uma configuração de solução. Os usuários podem criar suas próprias configurações de solução personalizada.  
  
 A tabela a seguir ilustra a configuração de configurações típicas de um projeto. As linhas são rotuladas com nomes de configuração e as colunas com nomes de plataforma.  
  
|Nome da configuração|Plataforma — Win32|Plataforma — Win64|  
|------------------------|----------------------|----------------------|  
|Depurar|\<Depurar configurações de Win32 >|\<Depurar configurações Win64 >|  
|Versão|\<Versão Win32 configurações >|\<Versão Win64 configurações >|  
|MyConfig|N/A|\<Configurações de MyConfig Win64 >|  
  
> [!NOTE]
>  Você não pode criar uma configuração de solução "MyConfig" que exclui uma plataforma "Win32", a menos que o projeto de que destino não oferece suporte a Win32.  
  
 Alterando a configuração ativa para uma solução seleciona o conjunto de configurações de projeto que são criadas, executar, depurar ou implantado na solução. Por exemplo, se você alterar a configuração de solução ativa de versão para depuração, todos os projetos na solução são criados automaticamente com a configuração de projetos indicada na configuração de depuração da solução. Configurações os projetos são normalmente também denominada depuração, a menos que o usuário tenha feito alterações manuais no Gerenciador de configuração do ambiente.  
  
 As propriedades de configuração de solução armazenadas para cada projeto incluem o nome do projeto, o nome de configuração do projeto, sinalizadores para indicar se deseja ou não para criar ou implantar e o nome da plataforma. Para obter mais informações, consulte [configuração da solução](../../extensibility/internals/solution-configuration.md).  
  
 O usuário pode exibir e definir parâmetros de configuração de solução, selecionando a solução na hierarquia (Gerenciador de soluções) e abrir as páginas de propriedades. Da mesma forma, você pode exibir e definir os parâmetros de configuração de projeto, selecionando um projeto no Solution Explorer e abrir as páginas de propriedades para o projeto.  
  
 O usuário também pode criar um projeto usando configurações de versão e os demais com configurações de depuração, se necessário. Para obter mais informações, consulte [configuração do projeto para criação de](../../extensibility/internals/project-configuration-for-building.md).  
  
 O diagrama a seguir mostra como as interfaces que dão suporte a configurações de solução e projeto são implementadas:  
  
 ![Gráfico de Interfaces de configuração](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuração  
  
 Algumas notas relacionadas ao diagrama anterior:  
  
-   `IDispatch`é marcado como opcional no objeto de configuração. Especificamente, é opcional para ter interfaces de configuração no objeto de procurar.  
  
-   `IVsDebuggableProjectCfg`está marcado como opcional no objeto de configuração, mas é necessário para suporte à depuração.  
  
-   `IVsProjectCfg2`está marcado como opcional no objeto de configuração, mas é necessária para suporte de agrupamento de saída.  
  
-   O `Config Provider` objeto está marcado como um objeto opcional, mas a opção é onde implementá-lo. Você pode implementar o objeto no objeto de projeto ou em um objeto separado.  
  
-   `IVsCfgProvider2`é necessário para suporte de plataforma e edição de configuração. `IVsCfgProvider`é suficiente se você implementar essa funcionalidade.  
  
-   Alguns desses objetos mostrados no diagrama como objetos separados podem ser combinados na mesma classe quando for prático com base nas necessidades específicas de design. Em outros tópicos desta seção, no entanto, os objetos e interfaces associadas a esses objetos serão discutidos acordo com o cenário apresentado no diagrama.  
  
-   Determinados objetos são implementados separadamente. Por exemplo, o projeto e construção da solução ocorrerem em threads separados e o objeto para gerenciar a vida de compilação separadamente do objeto que descreve a configuração para a compilação.  
  
 Para obter mais informações sobre as interfaces de objeto de configuração e as interfaces de objeto de provedor de configuração no diagrama anterior, consulte [o objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md). Além disso, [configuração do projeto para criação de](../../extensibility/internals/project-configuration-for-building.md) fornece mais informações sobre as interfaces de construtor de configuração e criar o objeto de dependência, e [configuração do projeto para gerenciamento de implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md) mais descreve as interfaces anexadas aos objetos de dependência de implantador e implantação de configuração. Por fim, [configuração do projeto para a saída](../../extensibility/internals/project-configuration-for-output.md) descreve as interfaces de objeto de saída e de grupo de saída e o uso das páginas de propriedades para exibir e definir propriedades dependentes de configuração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuração da solução](../../extensibility/internals/solution-configuration.md)
