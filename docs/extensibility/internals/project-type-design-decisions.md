---
title: "Decisões de Design de tipo de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
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
ms.openlocfilehash: 7bebb6ff1d9713298940ee4b26ccb61fee2835bd
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-design-decisions"></a>Decisões de Design de tipo de projeto
Antes de criar um novo tipo de projeto, você deve tomar várias decisões de design sobre o tipo de projeto. Você deve decidir quais tipos de itens que conterá seus projetos, como arquivos de projeto serão persistentes e qual modelo de compromisso que você usará.  
  
## <a name="project-items"></a>Itens de Projeto  
 Seu projeto usará arquivos ou objetos abstratos? Se você usar arquivos, eles será baseado no diretório ou referência de arquivos? São os arquivos ou objetos abstratos vão ser local ou remoto?  
  
 Os itens em um projeto podem ser arquivos, ou podem ser objetos mais abstratos, como objetos em um banco de dados repositório ou conexões de dados pela Internet. Se os itens são arquivos, o projeto pode ser uma base de referência ou um projeto com base no diretório.  
  
 Em projetos baseados em referências, itens podem aparecer em mais de um projeto. No entanto, o arquivo real que representa um item está localizado em um diretório somente. Em projetos baseados em diretório, todos os itens de projeto existem na estrutura do diretório. Para obter mais informações, consulte [NIB: Item Management in Projects](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Itens locais são armazenados no mesmo computador onde o aplicativo está instalado. Os itens remotos podem ser armazenados em um servidor separado em uma rede local ou em outro lugar na Internet.  
  
## <a name="project-file-persistence"></a>Persistência de arquivo de projeto  
 Serão armazenados os dados em sistemas de arquivo simples comuns ou em armazenamento estruturado? Arquivos serão abertos usando um editor padrão ou um editor específico do projeto?  
  
 Para manter seus dados, a maioria dos aplicativos salvam seus dados em um arquivo e, em seguida, lê-lo quando um usuário deve revisar ou alterar as informações.  
  
 Armazenamento estruturado, também chamado de arquivos compostos, normalmente é usado quando vários objetos de modelo de objeto de componente (COM) precisam armazenar seus dados persistentes em um único arquivo. Com o armazenamento estruturado, vários componentes de software diferentes podem compartilhar um arquivo de disco único.  
  
 Você tem várias opções a serem considerados em relação a persistência para os itens em seu projeto. Você pode executar qualquer uma das seguintes opções:  
  
-   Salve cada arquivo individualmente quando ela foi alterada.  
  
-   Capturar muitas transações em uma única **salvar** operação.  
  
-   Salvar arquivos localmente e publicar em um servidor ou usar outra abordagem para salvar itens de projeto quando o item representa uma conexão de dados para um objeto remoto.  
  
 Para obter mais informações sobre como persistência, consulte [projeto persistência](../../extensibility/internals/project-persistence.md) e [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modelo de projeto de compromisso  
 Objetos de dados persistentes ser abertos em modo direto ou transacionada?  
  
 Quando objetos de dados são abertos no modo direto, as alterações feitas nos dados são incorporadas imediatamente ou quando o usuário salva manualmente o arquivo.  
  
 Quando objetos de dados são abertos usando o modo de transação, as alterações são salvas em um local temporário na memória e não são confirmadas até que o usuário escolha manualmente salvar o arquivo. Nesse momento, todas as alterações devem ocorrer juntos ou nenhuma alteração será feita.  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Gerenciamento de PONTA: itens em projetos](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistência de projeto](../../extensibility/internals/project-persistence.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)   
 [Criando tipos de projeto](../../extensibility/internals/creating-project-types.md)
