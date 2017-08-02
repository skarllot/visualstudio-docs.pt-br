---
title: "Configuração de saída do projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
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
ms.openlocfilehash: 70be65424ef9f1a21ebbe91befbb8fee2e6dab2a
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-for-output"></a>Configuração de projeto para saída
Cada configuração pode dar suporte a um conjunto de processos de compilação que produzir saída itens como arquivos executáveis ou recurso. Esses itens de saída são privativos do usuário e podem ser colocados em grupos que vinculam tipos relacionados de saída, como arquivos executáveis (.exe. dll,. lib) e arquivos de origem (. idl, arquivos. h).  
  
 Itens de saída podem ser disponibilizados por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>métodos e enumerado com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> </xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> Quando você desejar agrupar itens de saída, seu projeto deve implementar também a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>  
  
 A construção desenvolvidos pela implementação `IVsOutputGroup` permite que os projetos saídas de grupo de acordo com o uso. Por exemplo, uma DLL pode ser agrupada com seu banco de dados do programa (PDB).  
  
> [!NOTE]
>  Um arquivo PDB contiver informações de depuração e é criada quando a opção 'Gerar informações de depuração' é especificada ao criar o arquivo. dll ou .exe. O arquivo. PDB normalmente é gerado para apenas a configuração de projeto de depuração.  
  
 O projeto deve retornar o mesmo número de grupos para cada configuração que ele suporta, mesmo que o número de saídas contido dentro de um grupo pode variar para cada configuração. Por exemplo, Matt do projeto DLL pode incluir mattd.dll e mattd.pdb na configuração de depuração, mas apenas incluir matt.dll na configuração de varejo.  
  
 Os grupos também têm as mesmas informações de identificador, como nome canônico, nome de exibição e informações de grupo de configuração dentro de um projeto. Essa consistência permite implantação e empacotamento para continuar a operar mesmo que alterar as configurações.  
  
 Grupos também podem ter uma saída de chave que permita atalhos de empacotamento apontar para algo significativo. Nenhum grupo pode ser vazio em uma determinada configuração, portanto não deve ser feita nenhuma suposição sobre o tamanho de um grupo. O tamanho (número de saídas) de cada grupo em qualquer configuração pode ser diferente do tamanho de outro grupo na mesma configuração. Ele também pode ser diferente do tamanho do mesmo grupo em outra configuração.  
  
 ![Gráfico de grupos de saída](~/extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupos de saída  
  
 O principal uso do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>interface é fornecer acesso para criar, implantar e depurar objetos de gerenciamento e permitir que os projetos a liberdade de grupo de saídas.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> Para obter mais informações sobre o uso dessa interface, consulte [o objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md).  
  
 No diagrama anterior, o grupo criado tem uma chave de saída em configurações (bD.exe ou b.exe), então o usuário pode criar um atalho para desenvolvido e saber que o atalho funcionará independentemente da configuração implantada. Origem do grupo não tem uma chave de saída, para que o usuário não pode criar um atalho para ele. Se a depuração grupo criado tem uma saída de chave, mas o grupo de varejo criados não, isso seria uma implementação incorreta. Ele segue, então, que se qualquer configuração tem um grupo que não contenha nenhuma saída, e, como resultado, nenhum arquivo de chave e outras configurações que contêm saídas com esse grupo não podem ter arquivos de chave. Os editores do instalador pressupõem a nomes canônicos e nomes de exibição dos grupos, além da existência de um arquivo de chave não são alterados com base em configurações.  
  
 Observe que, se um projeto tem um `IVsOutputGroup` que ele não deseja compactar ou implantar, é suficiente para não colocar essa saída em um grupo. A saída ainda pode ser enumerada normalmente Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>método que retorna todas as saídas da configuração, independentemente do agrupamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>  
  
 Para obter mais informações, consulte a implementação de `IVsOutputGroup` no exemplo de projeto personalizado em [MPF de projetos](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md)   
 [Configuração da solução](../../extensibility/internals/solution-configuration.md)
