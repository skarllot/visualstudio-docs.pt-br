---
title: "Estruturar sua solução de modelagem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 14
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b817affe78e53e0d010f5bb62676192fa90fd49e
ms.lasthandoff: 02/22/2017

---
# <a name="structure-your-modeling-solution"></a>Estruturar a solução de modelagem
Para usar modelos efetivamente em um projeto de desenvolvimento, os membros da equipe devem ser capazes de trabalhar em modelos de diferentes partes do projeto ao mesmo tempo. Este tópico sugere um esquema para dividir o aplicativo em partes diferentes que correspondem às camadas em geral diagrama em camadas.  
  
 Para iniciar em um projeto ou subprojeto rapidamente, é útil ter um modelo de projeto que segue a estrutura do projeto que você escolheu. Este tópico descreve como criar e usar o modelo.  
  
 Este tópico pressupõe que você está trabalhando em um projeto que seja grande o suficiente para exigir vários membros da equipe e talvez tenha várias equipes. O código e modelos do projeto são armazenados em um sistema de controle de origem, como [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Pelo menos alguns membros da equipe usam o Visual Studio para desenvolver modelos e outros membros da equipe podem exibir os modelos usando outras versões do Visual Studio.  
  
 Para ver quais versões do Visual Studio oferecer suporte a cada recurso da ferramenta e modelagem, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Estrutura da solução  
 Em um projeto de médio ou grande, a estrutura da equipe com base na estrutura do aplicativo. Cada equipe usa uma solução do Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>Para dividir um aplicativo em camadas  
  
1.  A estrutura de suas soluções de base na estrutura do seu aplicativo, como o aplicativo da web, aplicativo de serviço ou aplicativo da área de trabalho. Uma variedade de arquiteturas comuns é discutida em [aplicativo arquétipos no guia de arquitetura de aplicativo do Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2.  Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução, que chamaremos a solução de arquitetura. Essa solução será usada para criar o design geral do sistema. Ele contém modelos, mas nenhum código.  
  
     Adicione um diagrama de dependência para essa solução. No diagrama de dependência, desenhe a arquitetura que você escolheu para seu aplicativo. Por exemplo, o diagrama pode mostrar essas camadas e as dependências entre elas: apresentação; Lógica de negócios; e os dados.  
  
4.  Crie uma solução Visual Studio separada para cada camada no diagrama de dependência de arquitetura.  
  
     Essas soluções serão usadas para desenvolver o código das camadas.  
  
5.  Crie modelos que representarão os designs de camadas e os conceitos que são comuns a todas as camadas. Organize os modelos, de modo que todos os modelos podem ser vistos da solução de arquitetura e os modelos relevantes podem ser vistos de cada camada.  
  
     Você pode fazer isso usando qualquer um dos procedimentos a seguir. A primeira alternativa cria um projeto de modelagem separado para cada camada, e o segundo cria um projeto de modelagem única que é compartilhado entre as camadas.  
  
    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Para usar um projeto de modelagem separado para cada camada  
  
    1.  Crie um projeto de modelagem na solução de cada camada.  
  
         Este modelo contém diagramas que descrevem os requisitos e design dessa camada. Ele também pode conter diagramas de dependência que mostram camadas aninhadas.  
  
         Agora você tem um modelo para cada camada, além de um modelo para a arquitetura do aplicativo. Cada modelo é contido em sua própria solução. Isso permite que os membros da equipe trabalhar nas camadas ao mesmo tempo.  
  
    2.  Para a solução de arquitetura, adicione o projeto de modelagem de cada solução de camada. Para fazer isso, abra a solução de arquitetura. No Solution Explorer, clique com botão direito no nó da solução, aponte para adicionar e, em seguida, clique em **projeto existente**. Navegue para o projeto de modelagem (. modelproj) na solução de uma camada.  
  
         Cada modelo agora está visível em duas soluções: sua solução de "home" e a solução de arquitetura.  
  
    3.  Para o projeto de modelagem de cada camada, adicione um diagrama de dependência. Comece com uma cópia do diagrama de dependência da arquitetura. Você pode excluir as partes que não são as dependências do diagrama de dependência.  
  
         Você também pode adicionar diagramas de dependência que representam a estrutura detalhada dessa camada.  
  
         Esses diagramas são usados para validar o código desenvolvido nessa camada.  
  
    4.  Na solução de arquitetura, edite os requisitos e modelos de design de todas as camadas usando o Visual Studio.  
  
         Em cada solução de camada, desenvolva o código para essa camada, referindo-se ao modelo. Se você for fazer o desenvolvimento sem usar o mesmo computador para atualizar o modelo de conteúdo, você pode ler o modelo e desenvolver o código usando versões do Visual Studio que não é possível criar modelos. Você também pode gerar o código do modelo nessas versões.  
  
     Esse método garante que nenhuma interferência será causada pelos desenvolvedores que editar os modelos de camada ao mesmo tempo.  
  
     No entanto, como os modelos são separados, é difícil para se referir aos conceitos comuns. Cada modelo deve ter sua própria cópia dos elementos na qual é dependente de outras camadas e a arquitetura. O diagrama de dependência em cada camada deve ser mantido em sincronia com o diagrama de dependência de arquitetura. É difícil manter a sincronização quando alterar esses elementos, embora você possa desenvolver ferramentas para fazer isso.  
  
    ###### <a name="to-use-a-separate-package-for-each-layer"></a>Para usar um pacote separado para cada camada  
  
    1.  Na solução de cada camada, adicione o projeto de modelagem de arquitetura. No Solution Explorer, clique com botão direito no nó da solução, aponte para **adicionar**e, em seguida, clique em **projeto existente**. O projeto de modelagem única agora pode ser acessado de cada solução: o projeto de arquitetura e projeto de desenvolvimento de cada camada.  
  
    2.  No modelo compartilhado, crie um pacote para cada camada: no Solution Explorer, selecione o projeto de modelagem. No Gerenciador de modelos UML, clique no nó raiz modelo, aponte para **adicionar**e, em seguida, clique em **pacote**.  
  
         Cada pacote contém diagramas que descrevem os requisitos e design da camada correspondente.  
  
    3.  Se necessário, adicione diagramas de dependência local para a estrutura interna de cada camada.  
  
     Esse método permite que os elementos de design de cada camada para referir-se diretamente das camadas de arquitetura comum dos quais ele depende.  
  
     Embora o trabalho simultâneo em pacotes diferentes pode causar alguns conflitos, eles são bastante fácil de gerenciar porque os pacotes são armazenados em arquivos separados.
  
## <a name="creating-architecture-templates"></a>Criando modelos de arquitetura  
 Na prática, você não criará todas as suas soluções do Visual Studio ao mesmo tempo, mas adicioná-los conforme o andamento do projeto. Você provavelmente também use a mesma estrutura de solução de projetos futuros.  Para ajudá-lo a criar novas soluções rapidamente, você pode criar um modelo de projeto ou solução. Você pode capturar o modelo em um Visual Studio Integration extensão (VSIX) para que seja fácil de distribuir e instalar em outros computadores.  
  
 Por exemplo, se você frequentemente usa soluções com camadas de apresentação, negócios e dados, você pode configurar um modelo que criará novas soluções que têm essa estrutura.  
  
#### <a name="to-create-a-solution-template"></a>Para criar um modelo de solução  
  
1.  [Baixe e instale o Assistente para exportação de modelo](http://go.microsoft.com/fwlink/?LinkId=196686), se você ainda não tiver feito isso.  
  
2.  Crie a estrutura da solução que você deseja usar como ponto de partida para projetos futuros.  
  
3.  Sobre o **arquivo** menu, clique em **exportar modelo como VSIX**. O **exportar modelo Assistente VSIX** é aberto.  
  
4.  Seguindo as instruções no assistente, selecione os projetos que você deseja incluir no modelo, forneça um nome e uma descrição para o modelo e especificar um local de saída.  
  
> [!NOTE]
>  O material neste tópico é abstraído e traduzido com o Visual Studio arquitetura ferramentas diretrizes, escrito pelo Visual Studio ALM Rangers, que é uma colaboração entre Most Valued Professionals (MVPs), Microsoft Services e a equipe de produto do Visual Studio e gravadores. [Clique aqui para baixar o pacote de diretrizes completo.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Material relacionado  
 [Organizar e gerenciar seus modelos](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - vídeo por Clint Edmondson.  
  
 [Ferramentas diretrizes do Visual Studio arquitetura](../modeling/visual-studio-architecture-tooling-guidance.md) – mais orientações sobre gerenciamento de modelos em uma equipe  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)

