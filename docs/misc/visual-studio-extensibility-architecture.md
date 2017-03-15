---
title: "Arquitetura de extensibilidade do Visual Studio | Microsoft Docs"
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
  - "Visual Studio, o modelo de ambiente"
  - "modelo de ambiente, o Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Arquitetura de extensibilidade do Visual Studio
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado \(IDE\) é uma estrutura para hospedagem VSPackages e facilitando a troca de serviços compartilhados.  Um exemplo disso é a maneira que o IDE implementa a interface de usuário \(UI\).  O IDE fornece a janela de contêiner e as barras de ferramentas padrão e os menus.  Ele também fornece uma infra\-estrutura COM rica que torna a interface do usuário programável.  O esquema de roteamento e manipulação de comando completo fornece aos usuários uma estrutura aberta que oferece acesso fácil a ambos os existentes e instaladas de conjuntos de comandos.  
  
## Arquitetura de extensibilidade  
 A ilustração a seguir mostra a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arquitetura de extensibilidade.  Observe que o conceito de um aplicativo de software está ausente.  Em vez disso, os componentes de software de hosts do IDE, chamado VSPackages, que fornecem a funcionalidade do aplicativo.  Essa funcionalidade, por sua vez, é compartilhada entre o IDE como serviços.  Os VSPackages oferecem serviços que usam a eles e outros VSPackages.  O padrão IDE também oferece uma ampla gama de serviços, tais como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornecem acesso à funcionalidade de janelas do IDE.  
  
 ![Gráfico de arquitetura do ambiente](../extensibility/internals/media/environment.png "environment")  
Visão generalizada da arquitetura Visual Studio  
  
 Observe que a relação entre os VSPackages e serviços é bidirecional.  Embora VSPackages utilizar serviços oferecidos por outras pessoas, elas também podem oferecer serviços de seus próprios por usar o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface.  Essa arquitetura baseada em serviços foi desenvolvido a partir da implementação do Microsoft ActiveX Designer, no qual um serviço é um grupo de interfaces relacionadas que executam uma tarefa.  A partir de um ponto de vista COM estrito, todas as interfaces de um serviço devem ser implementadas em uma única classe COM.  
  
 O padrão IDE oferece serviços importantes, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>, que são usados por VSPackages.  A tabela a seguir lista e descreve alguns desses serviços.  Para obter mais informações, consulte [Usando e fornecer serviços](../extensibility/using-and-providing-services.md).  
  
|Serviço IDE|Descrição|  
|-----------------|---------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornece acesso ao IDE serviços lidar com funcionalidade básica, VSPackages e registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece windowing básica e funcionalidade relacionados à interface do usuário no IDE, como a capacidade para criar ferramentas e janelas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece a funcionalidade básica de solução relacionados, como, por exemplo, a capacidade de enumerar os projetos, criar novos projetos e monitorar as alterações do projeto.|  
  
 Por causa de sua total integração por meio da interação de serviços compartilhados, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE e VSPackages são intimamente interdependentes.  No entanto, apesar de sua interação fechar terão responsabilidades diferentes.  
  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE é responsável para as seguintes tarefas:  
  
-   Fornecendo serviços essenciais para uso por VSPackages externos.  
  
-   Fornecendo uma interface programável que permite a participação com elementos de interface do usuário padrão.  
  
-   Criação de instâncias de VSPackages conforme exigido por ações do usuário ou por outros serviços do solicitantes VSPackages.  
  
-   Fornecendo serviços que tornam possível para a comunicação e coordenação entre os VSPackages.  
  
-   Gerenciando soluções e os arquivos necessários.  
  
-   Fornecendo gerenciamento de janelas.  
  
-   Fornecimento de roteamento de comandos e barras de comandos, como, por exemplo, menus, barras de ferramentas e menus de contexto.  
  
-   Coordenação de seleção, contexto e moeda.  
  
 Os VSPackages são responsáveis pelas seguintes tarefas:  
  
-   Execução de determinadas rotinas de inicialização e encerramento.  
  
-   Gravar as informações no registro, o que o IDE usa para carregar os VSPackages apropriados horários adequados.  
  
-   Oferecendo os serviços que são necessários para se comunicar com outros VSPackages.  
  
-   Fornecendo implementações de novos tipos de projeto, editores e designers.  
  
-   Fornecendo extensões para elementos internos da interface do usuário, como, por exemplo, itens de tarefas, itens de caixa de ferramentas e a caixa de diálogo Opções.  
  
## Consulte também  
 [Shell do Visual Studio](../extensibility/internals/visual-studio-shell.md)   
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Como: obter um serviço](../Topic/How%20to:%20Get%20a%20Service.md)