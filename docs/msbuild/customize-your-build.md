---
title: Personalizar seu build | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: pt-br
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Personalizar seu build
Nas versões do MSBuild anteriores à versão 15, se você desejasse fornecer uma propriedade nova e personalizada para projetos em sua solução, você precisava adicionar manualmente uma referência a essa propriedade para cada arquivo de projeto na solução. Ou você precisava definir a propriedade em um arquivo .props e, em seguida, explicitamente, importar o arquivo .props em todos os projetos na solução, entre outras coisas.

No entanto, agora você pode adicionar uma nova propriedade a todos os projetos em uma única etapa, definindo-a em um único arquivo chamado Directory.Build.props na raiz do seu repositório. Quando o MSBuild é executado, o Microsoft.Common.props pesquisa sua estrutura de diretório pelo arquivo Directory.Build.props (e o Microsoft.Common.targets procura o Directory.Build.targets). Se ele encontrar um, ele importa a propriedade. Directory.Build.props é um arquivo definido pelo usuário que fornece personalizações de projetos em um diretório.

## <a name="directorybuildprops-example"></a>Exemplo de Directory.Build.props
Por exemplo, se você desejasse habilitar todos os seus projetos para acessar o novo recurso **/deterministic** do Roslyn (que é exposto no destino do CoreCompile do Roslyn pela propriedade `$(Deterministic)`), poderia fazer o seguinte.

1. Crie um novo arquivo na raiz do seu repositório chamado Directory.Build.props.
2. Adicione o XML a seguir ao arquivo.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Execute o MSBuild. As importações do Microsoft.Common.props e Microsoft.Common.targets existentes do projeto encontram o arquivo e o importam.

## <a name="search-scope"></a>Escopo da pesquisa
Ao pesquisar um arquivo Directory.Build.props, o MSBuild percorre a estrutura de diretórios para cima de seu local de projeto ($(MSBuildProjectFullPath)), parando depois de localizar o arquivo Directory.Build.props. Por exemplo, se seu $(MSBuildProjectFullPath) for c:\users\username\code\test\case1, o MSBuild deve iniciar a pesquisa aí e depois pesquisar a estrutura do diretório para cima até localizar um arquivo Directory.Build.props, como na estrutura de diretório a seguir.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
O local do arquivo de solução é irrelevante para o Directory.Build.props.

## <a name="import-order"></a>Ordem de importação

O Directory.Build.props é importado muito no início no Microsoft.Common.props, portanto, as propriedades definidas posteriormente não estão disponíveis para ele. Portanto, evite fazer referência a propriedades que ainda não foram definidas (e, portanto, serão avaliada como vazias).

O Directory.Build.targets é importado do Microsoft.Common.targets depois de importar os arquivos .target dos pacotes do NuGet. Portanto, ele pode ser usado para substituir as propriedades e os destinos definidos na maior parte da lógica de build, mas às vezes pode ser necessário fazer personalizações dentro do arquivo de projeto após a importação final.

## <a name="see-also"></a>Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   

