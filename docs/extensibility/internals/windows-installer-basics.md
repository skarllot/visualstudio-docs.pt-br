---
title: "Noções básicas do Windows Installer | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
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
ms.openlocfilehash: 15f1c1fbe61eee429352a13d228aa82a34f911d3
ms.lasthandoff: 02/22/2017

---
# <a name="windows-installer-basics"></a>Noções básicas do Windows Installer
O Windows Installer instala e desinstala aplicativos ou produtos de software no computador do usuário, realizar essas tarefas em unidades chamadas de componentes do Windows Installer (às vezes chamados WICs ou apenas componentes). Um GUID que identifica cada WIC, que é a unidade básica de instalação e de configurações usando o Windows Installer de contagem de referência.  
  
 Para obter uma documentação abrangente do Windows Installer, consulte o tópico Platform SDK, [do Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Criação de um VSPackage  
 Windows Installer usa pacotes de instalação, que contêm informações que o Windows Installer precisa para instalar, desinstalar ou reparar um produto e executar a interface de usuário (UI) de configuração. Cada pacote de instalação inclui um arquivo. msi, que contém um banco de dados de instalação, um fluxo de informações de resumo e fluxos de dados de várias partes da instalação. Para usar o instalador, você deve criar uma instalação. Porque o instalador organiza instalações em torno do conceito de componentes e armazena informações sobre a instalação em um banco de dados relacional, o processo de criação de um pacote de instalação amplamente envolve as seguintes etapas:  
  
1.  Planeje sua configuração de criação para dar suporte a suas estratégias de lado a lado e controle de versão.  
  
2.  Identifica os recursos a serem apresentados aos usuários.  
  
3.  Organize o VSPackage e as dependências em componentes.  
  
4.  Preencha o banco de dados com informações de instalação.  
  
5.  Valide o pacote de instalação.  
  
 Esta documentação está relacionada principalmente com as primeira e terceira as etapas do processo. Durante essas etapas você organizar seus recursos de VSPackage em WICs para que você possa quadro o controle de versão e atendendo a estratégia para conta as versões subsequentes do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. As três etapas restantes são abordadas em detalhes na documentação do Windows Installer no SDK da plataforma.  
  
## <a name="key-terms"></a>Principais termos  
 Seguem as definições de termos importantes relacionados à tecnologia do Windows Installer.  
  
 Recurso  
 Arquivos, chaves do registro, atalhos, ou e assim por diante que pode ser instalado em um computador. Esses recursos são agrupados logicamente em componentes do Windows Installer.  
  
 Componente do Windows Installer (WIC)  
 A unidade básica de instalação que representa um agrupamento lógico de recursos relacionados que são instalados e desinstalados como uma unidade. Componentes do Windows Installer são identificados por uma ID de componente exclusivo, ou GUID. Além disso, o Windows Installer mantém sua referência de contagem no nível do WIC. Para obter flexibilidade máxima de controle de versão, inclua não mais de um recurso principal, como uma DLL, em um determinado WIC. Observe que depois de identificar e preencher um WIC, dê a ele um GUID e implantá-lo, você não pode alterar sua composição. Para obter mais informações, consulte [organizar aplicativos em componentes](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Pacote (pacote de redistribuição)  
 Uma unidade de implantação que consiste em um arquivo. msi e arquivos de origem externa ao qual este arquivo pode apontar. Um pacote contém todas as informações do Windows Installer precisa para executar a interface do usuário e para instalar ou desinstalar o aplicativo.  
  
 arquivo. msi  
 Um arquivo de armazenamento estruturado em COM que contém as instruções e os dados necessários para instalar um aplicativo. Cada pacote contém pelo menos um arquivo. msi. O arquivo. msi contém o banco de dados do instalador, um fluxo de informações de resumo e possivelmente uma ou mais transformações e os arquivos de origem interna. Arquivos a serem instalados podem ser compactados em um gabinete e armazenados em um fluxo no arquivo. msi ou armazenados, compactados ou descompactados fora do arquivo. msi na mídia de origem. Para obter mais informações, consulte [as extensões de arquivo do Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Imposição de regras do Windows Installer  
 Dois conjuntos de regras determinam a implantação de recursos por meio de componentes de instalação. Um conjunto de regras é mantido pelo Windows Installer, enquanto você deve aplicar o segundo conjunto como autor da instalação.  
  
> [!NOTE]
>  A imposição de regras do Windows Installer ocorre somente se você executar uma validação de seu arquivo. msi. No entanto, são evitaram para tratar essas regras como as práticas recomendadas. Para obter mais informações, consulte [Validando um banco de dados de instalação](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) e [validação do pacote](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Regras aplicadas pelo instalador  
  
-   Todos os arquivos em um determinado componente devem ser instalados no mesmo diretório. Por outro lado, os arquivos instalados para pastas diferentes devem pertencer para separar os componentes.  
  
-   Pode haver apenas um caminho de chave por componente. O caminho da chave é simplesmente um arquivo ou chave do registro que representa o componente inteiro.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilidades do provedor de componente  
  
-   Quaisquer dois recursos podem enviar separadamente em versões subsequentes devem existir em componentes separados. Recursos devem ser agrupados no mesmo componente apenas quando tiver certeza de que esses recursos nunca serão enviados separadamente. Na verdade, é recomendável que todos os recursos principais (DLLs, por exemplo) sempre existem no WICs separados. Para obter mais informações, consulte [definindo componentes do instalador](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Nenhum recurso de controle de versão nunca deve enviar em mais de um WIC.  
  
## <a name="see-also"></a>Consulte também  
 [O que acontece se as regras de componente são interrompidas?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
