---
title: Visual Studio Shell (integrado) | Documentos do Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
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
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrado)
Shell do Visual Studio integrado inclui o ambiente de desenvolvimento integrado (IDE), o depurador e a integração de controle do código-fonte. Nenhuma linguagem de programação é incluída. No entanto, o shell integrado fornecem uma estrutura que permite que você adicione linguagens de programação.  
  
 Shell do Visual Studio integrado é na verdade uma combinação de shell do Visual Studio isolada mais uma instalação adicional que incluem componentes específicos do shell integrado.  O aplicativo de shell integrado deve incluir os dois o shell isolado pacote redistribuível do [pacote redistribuível do Microsoft Visual Studio Shell (isolado)](http://go.microsoft.com/fwlink/?LinkId=616022) , bem como o pacote redistribuível do shell integrado de [pacote redistribuível do Microsoft Visual Studio Shell (integrado)](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Antes de poder acessar os pacotes redistribuíveis do shell isolado e integrado, você precisará preencher uma pesquisa de clientes breve.  Depois de preencher a pesquisa, você será direcionado para uma página com links de download do pacote redistribuível Visual Studio se conectar.  Você pode encontrar os links de download em visitas subsequentes ao site do Visual Studio se conectar no **programas | VISUAL STUDIO 2015 e ISOLADO SHELL integrado** guia.  
  
 Se você instalar o aplicativo de shell integrado no mesmo computador como uma versão completa do Visual Studio, os componentes do aplicativo serão integrados diretamente no Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Recursos do Shell integrado  
  
|||  
|-|-|  
|Área de recurso|Recurso|  
|Suporte ao idioma|-Nenhum|  
|IDE|<ul><li>Configurações<br /><br /> <ul><li>Criar configurações</li><li>Importar e exportar configurações</li><li>Redefinir configurações</li></ul></li><li>**Caixa de ferramentas** integração</li><li>**Lista de tarefas** integração</li><li>Integração de ajuda</li><li>**Opções de** caixa de diálogo</li><li>Gerenciamento de fontes e cores</li><li>**Saída** janela</li><li>**Comando** janela</li><li>Gerenciamento de janela</li><li>Associações de teclas, menus e comandos</li><li>Tempo de execução de linguagem específica do domínio (DSL)</li></ul>|  
|Sistema de projeto e tipos de projeto|-Soluções e pastas de solução<br />-Gerenciador de configuração solução<br />-Gerenciamento item<br />-Soluções projeto único e vários projetos<br />-Application Designer (Propriedades do projeto simplificado)<br />-Adicionar referência da Web<br />-Adicionar referência de serviço<br />Único projeto<br />-Tipos de projeto de site da Web<br />-Projetos de aplicativos web|  
|Build|-Etapas de compilação personalizada no IDE<br />-Pré-compilação para proteção de propriedade intelectual (IP)<br />-Assinatura de código<br />     MSBuild|  
|Editor|-Código de navegação ferramentas (localização unificada, definição de fonte, herança)<br />-Código de navegação<br />-IntelliSense<br />-Marcas inteligentes<br />-Refatoração<br />-Listagem muito<br />-Filtragem IntelliSense<br />-   **Definição de código** janela|  
|Designer|-Windows Presentation Foundation Designer<br />-Windows Forms Designer<br />-Web Designer e Editor de HTML|  
|Dados|-   **Gerenciador de servidores** (simplificado: somente os dados). Consulte a Observação 1.<br />-   **Fontes de dados** janela<br />-Todo o conjunto de controles de dados<br />-Editor de XML<br />-Associar dados a fonte de dados local (. MDF ou. MDB)<br />-Data bind para objeto<br />-Associação de dados serviço Web<br />-Data ligar ao servidor de banco de dados local<br />-Data ligar ao servidor de banco de dados remoto<br />-Ferramentas DDL para dados remotos<br />-   **Gerenciador de servidores** extensibilidade ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] exemplos)|  
|Depurador|-Depuração local. Consulte a Observação 2.<br />-Depuração gerenciada<br />-Local de depuração<br />-Anexar ao processo local<br />-Anexar ao processo remoto<br />-Delegado anônimo<br />-Domínios de aplicativo<br />-Depuração ASPX<br />-Atributos<br />-Quebrar durante a função eval<br />-Pontos de interrupção<br />-Restrições de ponto de interrupção<br />-Pilha de chamadas<br />-   **Comando** janela<br />-Depuração thread cruzado<br />-Dicas de dados<br />-Visualizador de dados<br />-Suporte a depurador assistentes de depuração gerenciados (MDAs)<br />-Suporte a depurador encaminhador de tipo<br />-Suporte a DTEEvents OTB<br />-JMC seletor<br />-Teste do depurador AppID (DBGCLR)<br />-Perfil depurador<br />-Ferramentas e opções de depurador<br />-Iterador de depuração<br />-Avaliação de expressão tempo de design<br />-C# o avaliador de expressão<br />-Desmontagem<br />-Editar e continuar<br />-Windows avaliador de expressão (inspeção, locais, Autos)<br />-Exceção auxiliar<br />-Exceções<br />-Execução<br />-Genéricos<br />-Obter a fonte correta<br />-Depuração/Cluster HPC<br />-Vários idiomas depuração integrada<br />-Depuração interoperabilidade<br />-Depuração just-in-time<br />-Local de depuração<br />-Depuração gerenciada<br />-Controle manual (janela de processos)<br />-Memória<br />-Suporte de minidespejo<br />-Módulos<br />-Depuração multiprocesso<br />-Depuração nativa<br />-Novo suporte de mecanismo de depuração<br />-Depuração de código otimizado<br />-Filtragem do windows saída<br />-Processo de hospedagem para depuração gerenciada<br />-Processos<br />-Quickwatch<br />-Registra<br />-Registros na pilha<br />-Depuração remota<br />-Valores de retorno<br />-Depuração de scripts<br />-Suporte do serviço fonte<br />-Segurança<br />Side-by-side<br />-SQL<br />-Servidor de símbolos<br />-Pontos de rastreamento<br />-Thread<br />-Visualizações<br />-Depurador do extensible Stylesheet Language Transformations (XSLT)|  
|Suporte de&64; bits|-depuração de 64 bits para código gerenciado e nativo, todos os idiomas<br />-suporte a x64 nativo|  
|Controle do código fonte (SCC)|-Integração de SCC básica. Consulte a Observação 3.<br />-Ferramentas e opções de verificação|  
|Extensibilidade|-Consumir componentes VSPackages e MEF|  
  
## <a name="notes"></a>Observações  
  
#### <a name="1-data-tools"></a>1. Ferramentas de Dados  
 O shell integrado inclui ferramentas de desenvolvimento de banco de dados, como suporte para extensibilidade de dados e a simplificada **Solution Explorer**. No entanto, Crystal Reports, relatórios SQL e SQL Server Express não serão incluído no shell integrado.  
  
#### <a name="2-debugging-support"></a>2. Depuração de suporte  
 O shell integrado inclui o mesmo mecanismo de depuração que está incluído na versão de comunidade do Visual Studio. O mecanismo de depuração inclui o depurador comum para código gerenciado e também recursos relacionados, como a execução, anexar, definir ponto de interrupção, editar e continuar e outros. No entanto, o mecanismo de depuração não oferecer suporte a depuração de banco de dados do SQL Server.  
  
 Embora o suporte para depuração nativa é incluído no pacote do depurador básico, você não pode estendê-lo para oferecer suporte a idiomas adicionais.  
  
#### <a name="3-source-code-control-integration"></a>3. Integração do controle de código fonte  
 O shell integrado fornece APIs para implementar o controle do código-fonte (SCC) e para fornecer o controle de origem comum baseado em MSSCCI componentes de integração.  
  
 Embora o SCC integração não é um recurso regular da edição do Visual Studio Pro, integração de SCC é fornecida no shell integrado.  
  
#### <a name="4-build-support"></a>4. Suporte à compilação  
 O shell integrado fornece suporte de compilação. Você pode encontrar informações sobre compilações no [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Recursos não incluídos no Shell integrado  
 A seguir está uma lista dos recursos que não estão incluídos no shell integrado:  
  
-   Designer de Classe  
  
-   [Proteção preemptiva - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Recursos de linguagem  
  
-   VSHost  
  
-   Nenhum linguagens do Visual Studio ou seus modelos de projeto associado ou modelos de item de projeto, são incluídos no shell integrado. Nenhum implementações específicas de idioma de outros recursos estão incluídas, para trechos de código do Visual Basic de exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo a visão geral do Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)
