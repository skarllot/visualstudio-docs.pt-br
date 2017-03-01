---
title: Manter os dados no arquivo de projeto MSBuild | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
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
ms.openlocfilehash: 019baca4dcc06b349bfc4e20bac027deb623adbb
ms.lasthandoff: 02/22/2017

---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Manter os dados no arquivo de projeto do MSBuild
Talvez seja necessário um subtipo de projeto manter dados específicos subtipo no arquivo de projeto para uso posterior. Um subtipo de projeto usa a persistência do arquivo de projeto para atender aos seguintes requisitos:  
  
1.  Mantenha os dados usados como parte da criação do projeto. (Para obter mais informações sobre o Microsoft Build Engine, consulte [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).) Informações relacionadas a compilação podem:  
  
    1.  Dados de configuração independente. Ou seja, os dados armazenados em elementos de MSBuild com condições em branco ou ausentes.  
  
    2.  Dados de configuração dependente. Ou seja, os dados armazenados em elementos de MSBuild condicionados para uma configuração de projeto específico. Por exemplo:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Mantenha os dados que não são relevantes para compilar. Esses dados podem ser expressos em XML de forma livre que não é validado em relação a um esquema XML.  
  
    1.  Dados de configuração independente.  
  
    2.  Dados de configuração dependente.  
  
## <a name="persisting-build-related-information"></a>Informações relacionadas à compilação persistentes  
 Persistência de dados úteis para a criação de um projeto é tratada pelo MSBuild. O sistema MSBuild mantém uma tabela mestre de informações relacionadas a compilação. Subtipos de projeto são responsáveis por acessar esses dados para obter e definir valores de propriedade. Subtipos de projeto também podem aumentar a tabela de dados relacionados à compilação Adicionando propriedades adicionais para ser persistente e remover propriedades de forma que eles não são persistentes.  
  
 Para modificar os dados do MSBuild, um subtipo de projeto é responsável por recuperar o objeto de propriedade MSBuild do sistema base projeto por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>é uma interface implementada no sistema de projeto principal e as consultas de subtipo agregação do projeto para ele executando `QueryInterface`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>  
  
 O procedimento a seguir descreve as etapas para remover uma propriedade usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para remover uma propriedade de um arquivo de projeto MSBuild  
  
1.  Chamar `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>do subtipo do projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>com `pszPropName` definido para a propriedade que deseja remover.</xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>  
  
### <a name="persisting-non-build-related-information"></a>Informações relacionadas a compilação não persistente  
 Persistência de dados em arquivos de projeto que não importa a compilação é tratada por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>  
  
 Você pode implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>em principal `project subtype aggregator` objeto, o `project subtype project configuration` ou ambos.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>  
  
 Os pontos a seguir descrevem os principais conceitos sobre a persistência de informações de compilação não relacionadas.  
  
-   Chama o projeto com base no objeto de agregador de subtipo (ou seja, o subtipo de projeto externo) projeto principal para carregar e salvar dados de configuração independente e ela chama os objetos de configuração de projeto do projeto subtipo ao carregar ou salvar os dados de configuração.  
  
-   O projeto base chama os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>várias vezes para cada nível de agregação de subtipo do projeto e passa o GUID para cada nível.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>  
  
-   O projeto base passa ou recebe um fragmento XML que é dedicado a um subtipo de projeto específico e usa esse mecanismo como uma maneira de persistir o estado entre os níveis de agregação.  
  
-   O projeto base chama o subtipo de projeto externo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementação passando um GUID.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Se o GUID pertence o subtipo de projeto externo, ele lida com a chamada propriamente dito; Caso contrário, ele delega a chamada para um subtipo de projeto interno e assim por diante, até encontra o subtipo de projeto que o GUID corresponde ao.  
  
-   Um subtipo de projeto também pode modificar o fragmento XML antes ou depois de ele delega a chamada para um subtipo de projeto interno. O exemplo a seguir mostra um trecho de um arquivo de projeto, onde um nome de um arquivo que contém propriedades específicas de um subtipo de projeto, é passado para esse subtipo de projeto.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)
