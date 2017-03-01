---
title: Visual Studio isolada Shell | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Visual Studio isolada Shell
Shell do Visual Studio isolado permite que você crie aplicativos autônomos que podem ser executados lado a lado com outras versões do Visual Studio. Ele é usado principalmente para hospedar ferramentas especializadas que podem usar os serviços do Visual Studio, mas também têm uma aparência personalizada e identidade visual. Recursos do Visual Studio e grupos de comando de menu podem facilmente ser ativados e desativado. Aplicativo títulos, ícones de aplicativo e telas de abertura são totalmente personalizáveis. Para obter uma lista de recursos personalizáveis, consulte [personalizar o Shell isolado](../extensibility/customizing-the-isolated-shell.md).  
  
 Para trabalhar com um projeto do shell isolado, você deve instalar o SDK do Visual Studio. A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Para criar um aplicativo de shell isolado, comece com um projeto do Visual Studio Shell isolado. Este projeto contém tudo o que você precisa para desenvolver e testar seu próprio aplicativo de shell isolado. Quando estiver pronto para escrever o programa de instalação que implanta seu aplicativo, você deve obter o pacote redistribuível do shell isolado do [pacote redistribuível do Microsoft Visual Studio Shell (isolado)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Antes de poder acessar o pacote redistribuível do shell isolado, você precisará preencher uma pesquisa de clientes breve.  Depois de preencher a pesquisa, você será direcionado para uma página com links de download do pacote redistribuível Visual Studio se conectar.  Você pode encontrar os links de download em visitas subsequentes ao site do Visual Studio se conectar no **programas | VISUAL STUDIO 2015 e ISOLADO SHELL integrado** guia.  
  
> [!NOTE]
>  Para obter mais informações sobre como implantar um aplicativo baseado no shell isolado, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabalhando com o shell isolado  
 Um aplicativo de shell do Visual Studio isolada tem acesso completo aos serviços do Visual Studio e oferece suporte a identidade visual e personalização especial. Há várias maneiras de personalizar um aplicativo de shell isolado:  
  
-   Você pode usar componentes VSPackages e Managed Extensibility Framework (MEF) para estender um aplicativo de shell isolado, assim como você usaria em qualquer outra extensão do Visual Studio. Para obter mais informações, consulte [estendendo o Shell isolado](../extensibility/extending-the-isolated-shell.md).  
  
-   Para tornar os recursos do Visual Studio e grupos de comando de menu disponível ou não, atualize o arquivo. VSCT no projeto de interface do usuário do aplicativo.  
  
-   Para remover **opções** páginas ou outros componentes do shell do Visual Studio do aplicativo, atualize o arquivo .pkgundef do aplicativo.  
  
-   Para modificar o comportamento do shell ou outros aspectos da aparência, atualize o arquivo pkgdef do aplicativo.  
  
-   Alguns aspectos do shell também podem ser especificados quando o aplicativo é iniciado. Para fazer isso, atualize os parâmetros na chamada para o ponto de entrada inicial do appenvstub.dll.  
  
 Para obter mais informações sobre os diferentes elementos que você pode personalizar, consulte [elementos do Shell isolado](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Recursos padrão do Shell isolado  
 Os seguintes recursos são padrão para todas as edições do Visual Studio.  
  
|Categoria de Recurso|Recurso|  
|----------------------|-------------|  
|Recursos de IDE|Configurações de importação/exportação<br /><br /> Instalador de controle de caixa de ferramentas<br /><br /> Lista de tarefas < / lista de erros<br /><br /> Janela Saída<br /><br /> Start Page<br /><br /> Janela Propriedades<br /><br /> Caixa de Ferramentas<br /><br /> Gerenciador de Soluções<br /><br /> Janela de Indicadores<br /><br /> Exibição de Classe<br /><br /> Pesquisador de Objetos<br /><br /> Janela Comando<br /><br /> Estrutura de Tópicos do Documento<br /><br /> Modo de Exibição de Recursos<br /><br /> Ferramenta externa<br /><br /> Windows Communication Foundation (WCF) adicionar referência de serviço<br /><br /> Language Integrated Query (LINQ) suporte|  
|Editor/Designer|Código de navegação ferramentas (localização unificada, definição de fonte, herança)<br /><br /> IntelliSense<br /><br /> Marcas inteligentes<br /><br /> Gerenciador de Trechos de Código<br /><br /> Trechos de código<br /><br /> Refatoração<br /><br /> Listagem muito<br /><br /> Filtragem IntelliSense<br /><br /> Janela de Definição de Código<br /><br /> Designer de aplicativos<br /><br /> Designer de Formulários do Windows<br /><br /> Designer do Windows Presentation Foundation (WPF)|  
|Depuração|Avaliador de expressão c#<br /><br /> Depuração local<br /><br /> Depuração gerenciada<br /><br /> Editar e continuar<br /><br /> Depuração de thread cruzado<br /><br /> Visualizações<br /><br /> DataTips<br /><br /> Depuração nativa<br /><br /> Depuração de script<br /><br /> Depuração Interop<br /><br /> Depuração Just-in-time (JIT)<br /><br /> Depuração multiprocesso<br /><br /> Depuração de XSLT<br /><br /> Anexar ao processo local<br /><br /> Pontos de rastreamento<br /><br /> Restrições de ponto de interrupção|  
|Dados|Gerenciador de servidores (simplificado - somente dados)<br /><br /> Associar dados a dados local (. MDF ou. MDB)<br /><br /> Associar dados ao objeto<br /><br /> Vincular dados ao serviço Web<br /><br /> Conjunto completo de controles de dados<br /><br /> Editor de XML<br /><br /> Ligação de dados ao servidor de banco de dados local<br /><br /> janela Fontes de Dados|  
|Web|Editor de HTML<br /><br /> Navegador da Web<br /><br /> O Web Forms designer<br /><br /> Projeto de Site<br /><br /> Projeto de Aplicativo Web|  
|Extensibilidade|Consome componentes VSPackages e MEF|  
  
## <a name="see-also"></a>Consulte também  
 [Shell (isolado ou integrado)](../extensibility/shell-isolated-or-integrated.md)
