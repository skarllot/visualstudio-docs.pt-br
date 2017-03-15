---
title: "Descrição do modelo do diretório (. Arquivos Vsdir) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: 8
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
ms.openlocfilehash: f906ffc0ae022870a42cb671b27464c72278e955
ms.lasthandoff: 02/22/2017

---
# <a name="template-directory-description-vsdir-files"></a>Descrição do modelo do diretório (. Arquivos Vsdir)
Um arquivo de descrição de pasta do modelo (. vsdir) é um arquivo de texto que permite que o ambiente de desenvolvimento integrado (IDE) para exibir pastas, arquivos. vsz do assistente e arquivos de modelo que estão associados ao seu projeto em caixas de diálogo. O conteúdo inclui um registro por arquivo ou pasta. Todos os arquivos. vsdir em um local de referência são mesclados, embora. vsdir apenas um arquivo geralmente é fornecido para descrever várias pastas, assistentes ou arquivos de modelo.  
  
 Pastas (subpastas), os arquivos referenciados no arquivo. vsdir e o próprio arquivo. vsdir estão localizadas no mesmo diretório. Quando o IDE executa um assistente ou exibe uma pasta ou arquivo de **novo projeto** ou **Adicionar Novo Item** caixas de diálogo, o IDE examina o diretório que contém os arquivos executados para determinar se um arquivo. vsdir está presente. Se um arquivo. vsdir for encontrado, o IDE lê-lo para determinar se ele contém uma entrada para o arquivo ou pasta executada ou exibida. Se uma entrada for encontrada, o IDE usa as informações na tela do conteúdo ou a execução do assistente.  
  
 O exemplo de código a seguir está no arquivo de SourceFiles.vsdir no \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files chave de registro:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 Nesse caso, dois registros estão em um arquivo. Uma nova linha (caractere de retorno de carro) separa cada registro. Cada linha representa um tipo de arquivo diferente. Um caractere de pipe (|) separa campos em cada registro. Um único diretório pode conter vários arquivos. vsdir com nomes de arquivo diferentes, ou você pode ter um arquivo. vsdir para cada tipo de arquivo.  
  
## <a name="fields"></a>Campos  
 A tabela a seguir lista os campos especificados para cada registro.  
  
|Campo|Descrição|  
|-----------|-----------------|  
|Nome de caminho relativo (RelPathName)|O nome do arquivo. vsz, modelo ou pasta, como HeaderFile.h ou MyWizard.vsz. Esse campo também pode ser um nome usado para representar uma pasta.|  
|{clsidPackage}|O GUID do VSPackage que permite o acesso às cadeias de caracteres localizadas, como LocalizedName, descrição, IconResourceId e SuggestedBaseName, nos recursos do VSPackage satélite dynamic link library (DLL). IconResourceId se aplica se DLLPath não for fornecido. **Observação:** esse campo é opcional, a menos que um ou mais dos campos anteriores é um identificador de recurso. Este campo é normalmente em branco para arquivos. vsdir que correspondem aos assistentes de terceiros que não localizar o texto.|  
|LocalizedName|O nome localizado do arquivo de modelo ou assistente. Este campo pode ser uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". Esse nome é exibido no **Adicionar Novo Item** caixa de diálogo. **Observação:** se LocalizedName é um identificador de recurso, {clsidPackage} é necessário.|  
|SortPriority|Um inteiro que representa a prioridade relativa desse arquivo de modelo ou assistente. Por exemplo, se este item tem um valor de 1, esse item é exibido ao lado de outros itens com um valor de 1 e à frente de todos os itens com um valor de classificação 2 ou maior.<br /><br /> Prioridade de classificação é relativo os itens no mesmo diretório. Pode haver mais de um arquivo. vsdir no mesmo diretório. Nesse caso, os itens de todos os *.* arquivos vsdir nesse diretório são mesclados. Itens com a mesma prioridade são listados em ordem lexicográfica maiusculas e minúsculas do nome exibido. O `_wcsicmp` função é usada para ordenar os itens.<br /><br /> Os itens não são descritos em arquivos. vsdir incluem um número de prioridade maior que o número de prioridade mais alto listado nos arquivos. vsdir. O resultado é que esses itens estão no final da lista exibida, independentemente de seu nome.|  
|Descrição|A descrição localizada do arquivo de modelo ou assistente. Este campo pode ser uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". Essa cadeia de caracteres aparece no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo quando o item é selecionado.|  
|DLLPath ou {clsidPackage}|Usado para carregar um ícone para o assistente ou um arquivo de modelo. O ícone é carregado como um recurso de um arquivo. dll ou .exe usando o IconResourceId. Esse arquivo. dll ou .exe pode ser identificado usando um caminho completo ou usando uma GUID de um VSPackage. A implementação de DLL do VSPackage é usada para carregar o ícone (não a DLL satélite).|  
|IconResourceId|O identificador de recurso na implementação da DLL ou VSPackage DLL que determina o ícone a ser exibido.|  
|Sinalizadores (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)</xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>|Usado para desabilitar ou habilitar o **nome** e **local** campos de **Adicionar Novo Item** caixa de diálogo. O valor de **sinalizadores** campo é o equivalente decimal da combinação de sinalizadores de bit necessário.<br /><br /> Quando um usuário seleciona um item no **novo** guia, o projeto determina se os campos de nome e o local são mostrados quando o **Adicionar Novo Item** caixa de diálogo é exibida primeiro. Um item, por meio de um arquivo. vsdir, pode controlar somente se os campos estão habilitados versus desabilitado quando o item é selecionado.|  
|SuggestedBaseName|Representa o nome padrão para o arquivo, o assistente ou o modelo. Esse campo é uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". O IDE usa esse valor para fornecer um nome padrão para o item. Esse valor base é acrescentado com um valor inteiro para tornar o nome exclusivo, como MyFile21.asp.<br /><br /> Na lista anterior, descrição, DLLPath, IconResourceId, sinalizadores e SuggestedBaseNumber aplicam-se somente a arquivos de modelo e o assistente. Esses campos não se aplicam às pastas. Esse fato é ilustrado no código no arquivo BscPrjProjectItems o \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems chave de registro. Este arquivo contém três registros (um para cada pasta) com quatro campos para cada registro: RelPathName, {clsidPackage} LocalizedName e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Quando você cria um arquivo do assistente, você também deve considerar os seguintes problemas.  
  
-   Qualquer campo não é necessário para o qual não há nenhum dado significativo deve conter um 0 (zero) como um espaço reservado.  
  
-   Se nenhum nome localizado for fornecido, o nome de caminho relativo é usado no arquivo do assistente.  
  
-   DLLPath substitui clsidPackage para o local do ícone.  
  
-   Se nenhum ícone for definido, o IDE substitui o ícone padrão para um arquivo que tem a extensão.  
  
-   Se nenhum nome de base sugerido for fornecido, 'Projeto' será usado.  
  
-   Se você excluir os arquivos. vsz, pastas ou arquivos de modelo, você também deve remover seus registros associados do arquivo. vsdir.  
  
## <a name="see-also"></a>Consulte também  
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
