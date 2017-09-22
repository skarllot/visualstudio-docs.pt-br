---
title: "Caixa de diálogo Configurações do Projeto VC++, Projetos e Soluções, Opções | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
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
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 6980c103c58df6ef88837c8701be2e04ccb0eee2
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Caixa de diálogo Configurações do Projeto do VC++, Projetos e Soluções, Opções
Esta caixa de diálogo permite que você defina o build de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e configurações de projeto relacionadas ao log de build e tipos de arquivo de suporte.  
  
### <a name="to-access-this-dialog-box"></a>Para acessar essa caixa de diálogo  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Selecione **Projetos e Soluções** e, em seguida, selecione **Configurações do Projeto VC++**.  
  
 
## <a name="build-logging"></a>Log de build  
 **Sim**  
  Ativa a geração de arquivo de log de build. Essa opção gera o BuildLog.htm, que pode ser encontrado no diretório de arquivos intermediários do projeto. Cada novo build substitui o arquivo BuildLog.htm anterior.  
  
 **No**  
  Desativa a geração de arquivo de log de build.  

## <a name="show-environment-in-log"></a>Mostrar ambiente em log  
 **Sim**  
 Lista as variáveis de ambiente no arquivo de log de build. Essa opção específica o eco para todas as variáveis de ambiente, durante os builds dos projetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], para o arquivo de log de build.  
  
 **No**  
 Exclua as variáveis de ambiente do arquivo de log de build.  

## <a name="build-timing"></a>Tempo de build  
 **Sim**  
  Ativa o tempo de build. Se selecionado, o tempo necessário para a conclusão do build é publicado na Janela de Saída. Para obter mais informações, consulte [Janela de Saída](../../ide/reference/output-window.md).  
  
 **No**  
 Desativa o tempo de build.  
   
## <a name="maximum-concurrent-c-compilations"></a>Máximo de compilações simultâneas C++  
  Especifica o número máximo de núcleos de CPU a serem usados para a compilação C++ paralela.  
  
## <a name="extensions-to-include"></a>Extensões a serem incluídas  
  Especifica as extensões de nome de arquivo dos arquivos que podem ser portados em seu projeto.  

## <a name="extensions-to-hide"></a>Extensões a serem ocultadas  
  Especifica as extensões de nome de arquivo dos arquivos que não serão exibidos no **Gerenciador de Soluções** quando **Mostrar Todos os Arquivos** for habilitado.  

 ## <a name="build-customization-search-path"></a>Caminho de pesquisa de personalização do build  
  Especifica a lista de diretórios que contêm arquivos de .rules, que o ajudarão a definir regras de build para seus projetos.  

# <a name="solution-explorer-mode"></a>Modo do Gerenciador de Soluções  
 **Mostrar somente arquivos no projeto**  
  Configura o **Gerenciador de Soluções** para exibir apenas os arquivos no projeto.  
  
 **Mostrar todos os arquivos**  
  Configura o **Gerenciador de Soluções** para mostrar os arquivos no projeto e nos arquivos em disco na pasta do projeto.  


## <a name="enable-project-caching"></a>Habilitar Cache de Projeto
**Sim** Permite que o Visual Studio coloque em cache os dados de projeto, para que, quando você abrir o projeto na próxima vez, ele possa carregar esses dados armazenados em cache em vez de recalcular dos arquivos de projeto. Usar dados armazenados em cache pode acelerar significativamente o tempo de carregamento do projeto.   

**Não** Não usar dados armazenados em cache do projeto. Analisar os arquivos de projeto cada vez que o projeto é carregado.


  

  
#
## <a name="see-also"></a>Consulte também  
 [Compilando programas C/C++](/cpp/build/building-c-cpp-programs)   
 [Referência de build C/C++](/cpp/build/reference/c-cpp-building-reference)
