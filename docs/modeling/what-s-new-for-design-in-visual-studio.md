---
title: Novidades no design no Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
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
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>Novidades no design no Visual Studio

## <a name="live-dependency-validation"></a>Validação de dependência em tempo real

Removendo dependências indesejáveis é uma parte importante do gerenciamento de suas deficiências técnicas.
Validação em tempo real das dependências é agora incluída, fornecendo informações precisas sobre problemas e se beneficiar totalmente com os novos recursos na lista de erros e o editor.

![Validação de dependência ao vivo em ação](~/docs/modeling/media/dep-validation-whatsnew-01.png)

A experiência de criação foi alterado para fazer a validação de dependência mais detectáveis e mais acessível, alterando a terminologia de "Diagrama de camada" para "Diagrama de dependência".

O **arquitetura** menu agora contém um comando para criar um diagrama de dependência diretamente:

![Item de dependência ao vivo no menu de arquitetura](~/docs/modeling/media/dep-validation-whatsnew-02.png)

... e os nomes de propriedade de uma camada em um diagrama de dependência e suas descrições, foram alterados para torná-los mais significativos:

![Nomes de propriedade de dependência ao vivo atualizado](~/docs/modeling/media/dep-validation-whatsnew-03.png)

Agora você ver o impacto das alterações imediatamente nos resultados da análise para o código na solução atual sempre que você salvar o diagrama. Você não precisa mais esperar pela conclusão do comando "Validar dependências".

Para obter mais detalhes, consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>Designers UML foram removidos

Os designers UML foram removidos desta versão do Visual Studio Enterprise.

* Diagramas UML agora são apresentados como arquivos XML
* O Gerenciador de modelos UML não existe
* Referências não são mais usadas para validação de dependência de projeto de modelagem
* O nó de "Referências de camada" no Gerenciador de soluções não é mais exibido
* A ação de compilação "Validação" em um diagrama de dependência (camada) não é mais usada - a tarefa de compilação foi removida 
* A estrutura do projeto é mantida para o ciclo completo entre versões
* Você ainda pode abrir, criar, editar e salvar um diagrama de dependência (camada) como XML
* Itens de trabalho do TFS vinculados a um diagrama de dependência (camada) não estão acessíveis na superfície de design
* Não há suporte para a vinculação voltar de DSL ou uma camada 
* Não há suporte para extensibilidade o SDK de modelagem UML

Entretanto, há suporte para visualizar a arquitetura do código .NET e C++ está disponível por meio de [mapas de código](map-dependencies-across-your-solutions.md)e os aperfeiçoamentos significativos para validação de dependência descrito acima.

Se você for um usuário significativo dos designers UML, você pode continuar a usar o Visual Studio 2015 ou versões anteriores enquanto você decidir sobre uma ferramenta alternativa para suas necessidades UML.

Para obter mais detalhes, consulte [esta postagem de blog](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Suporte de versão para a arquitetura e ferramentas de modelagem  

O Visual Studio está disponível em várias versões. Nem todos eles oferecem suporte para a arquitetura e ferramentas de modelagem. A tabela a seguir mostra a disponibilidade de cada ferramenta.  
  
|**Recurso**|**Enterprise**|**Professional**|**Comunidade**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Mapas de código**|Sim|Consulte a Observação (1)|-|-|  
|**Diagramas de dependência**|Sim|Consulte a Observação (2)|Consulte a Observação (2)|-|  
|**Direcionado gráficos** (diagramas DGML)|Sim|Sim|Sim|-|  
|**Clone de código**|Sim|-|-|-|  
  
Observação (1): Suporta apenas ler mapas de código, filtragem de mapas de código, adicionar novos nós genéricos e criando um novo gráfico direcionado a partir de uma seleção.

Observação (2): Tem suporte apenas para leitura de diagramas de dependência.

