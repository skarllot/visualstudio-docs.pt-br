---
title: Designer de manifesto VSIX | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
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
ms.openlocfilehash: 35aac8c70204590a3a856d1c97dc31249fb16af7
ms.lasthandoff: 02/22/2017

---
# <a name="vsix-manifest-designer"></a>Designer de manifesto VSIX
Modifica um pacote manifesto arquivo VSIX, que define o comportamento da instalação de uma extensão do Visual Studio.  
  
 O **Designer de manifesto VSIX** mapeia para o esquema subjacente do VSIX. Cada elemento no esquema pode ser definido usando um controle correspondente no designer. Para obter mais informações sobre o esquema, consulte [VSIX extensão de esquema 2.0 referência](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Para abrir o **Designer de manifesto VSIX**, localize um arquivo source.extension.vsixmanifest **Solution Explorer**e abra o arquivo. Se o arquivo não contém XML válido, o designer de manifesto não será aberto.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest é enviado para vsixmanifest quando o pacote for criado.  
  
## <a name="uielement-list"></a>Lista UIElement  
 O **Designer de manifesto VSIX** contém quatro seções que correspondem a esses elementos de nível superior do esquema:  
  
-   Metadados  
  
-   Instalar destinos  
  
-   Ativos  
  
-   Dependências  
  
 A área de título contém os seguintes controles.  
  
 **Nome do produto**  
 Descreve o nome da extensão.  
  
 **ID do produto**  
 Especifica as informações de identificação exclusivo para este pacote.  
  
 **Autor**  
 Especifica o nome do autor da extensão.  
  
 **Versão**  
 Especifica o número de versão da extensão.  
  
 O **metadados** guia contém os seguintes controles.  
  
 **Descrição**  
 Fornece uma descrição de texto da extensão a ser exibido no **Extension Manager**.  
  
 **Linguagem**  
 Especifica o idioma padrão para o pacote, que corresponde aos dados textuais no manifesto. O `Language` atributo segue a convenção de código localidade common language runtime (CLR) para módulos de recursos, por exemplo, en-us, en, fr-fr. Por padrão, o valor é neutro; Isso significa que o pacote será executado em qualquer versão de idioma do Visual Studio.  
  
 **Licença**  
 Especifica o arquivo de texto que contém a licença de usuário, se houver.  
  
 **Ícone**  
 Especifica o arquivo gráfico (. png,. bmp,. JPEG,. ico) que contém o ícone a ser exibido no **Extension Manager**, se houver um ícone. A imagem de ícone deve ter 32 x 32 pixels ou será redimensionada para essas dimensões. Se nenhum ícone for especificado, **Extension Manager** usa um ícone padrão.  
  
 **Imagem de visualização**  
 Especifica o arquivo gráfico (. png,. bmp,. JPEG,. ico) que contém a imagem a ser exibida em **Extension Manager**, se houver uma imagem de visualização. A imagem de visualização deve ser 200 x 200 pixels. Se nenhuma imagem de visualização for especificada, **Extension Manager** usa uma imagem padrão.  
  
 **Marcas**  
 Adiciona marcas de texto a ser usado para dicas de pesquisa.  
  
 **Notas de versão**  
 Especifica um arquivo (. txt,. rtf) que contém as notas de versão. Também usa a URL de um site da Web que exibe as notas de versão.  
  
 **Guia de Introdução**  
 Especifica um arquivo (. txt,. rtf) que contém informações sobre como usar a extensão ou o conteúdo do pacote VSIX. Este guia é exibida quando a instalação da extensão estiver concluída. Também usa a URL de um site da Web que exibe o guia.  
  
 **URL para mais informações**  
 Especifica a URL de um site que contém informações adicionais sobre o produto.  
  
 O **instalar destinos** guia contém os seguintes controles.  
  
 **Tipo de instalação**  
 Lista **extensão do Visual Studio** e **SDK de extensão** como tipos de instalação de destino. As opções diferem, dependendo do tipo que você escolher.  
  
 **Extensão do Visual Studio**  
 Lista de **InstallationTarget** elementos que descrevem como o pacote pode ser instalado e em quais produtos do Visual Studio esta extensão pode ser instalada. Cada produto é identificado separadamente por nome e uma versão ou intervalo.  Produtos podem ser adicionados à lista, modificados e excluídos. O nome e a versão de um produto correspondem do **Id** e **versão** atributos de associado **InstallationTarget** elemento.  
  
 **Intervalo de versão** é [12.0, 14.0] e usa a notação a seguir:  
  
-   [– inclusive de versão mínima  
  
-   ] – inclusive de versão máxima  
  
-   (-exclusivo de versão mínima  
  
-   ) – versão máxima exclusivo  
  
-   Única versão # - somente a versão especificada  
  
 **SDK de extensão**  
 Especifica uma instalação global que não está no escopo de um produto específico e a versão. **Identificador de plataforma de destino** é a plataforma, como "Windows", que você deseja. **Versão da plataforma de destino** é a versão, como 8.0, a plataforma de destino. **Nome do SDK** e **SDK versão** é o nome e o número da versão do SDK, respectivamente.  
  
 **Este VSIX está instalado para todos os usuários (exige a elevação em instalar)** caixa de seleção  
 Se esta caixa de seleção estiver marcada, essa extensão é instalada para todos os usuários; Caso contrário, ele é instalado apenas para o usuário atual.  
  
 **Este VSIX é instalado pelo Windows Installer** caixa de seleção  
 Se esta caixa de seleção estiver marcada, essa extensão é instalada pelo Windows Installer (arquivo. msi); Caso contrário, ele é instalado como um pacote VSIX típico (arquivo. VSIX).  
  
 O **ativos** guia contém os seguintes controles.  
  
 **Lista de ativos**  
 Lista os elementos ativos que descrevem os elementos de extensão ou o conteúdo desse pacote superfícies. Cada extensão ou elemento de conteúdo é listado separadamente por origem, o tipo e o caminho. Elementos de conteúdo e as extensões podem ser adicionados à lista, modificados e excluídos. O tipo e o caminho de um elemento de extensão ou conteúdo corresponde do `Type` e `Path` atributos de associado `Asset` elemento. Os seguintes tipos são conhecidos:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Para adicionar ou editar um ativo, você deve especificar o tipo de ativo, se o ativo é um projeto na solução atual ou um arquivo no sistema de arquivos e o nome do projeto. Você também pode especificar o nome da pasta na qual deve ser inserido.  
  
 Você também pode criar seus próprios tipos e dar-lhes nomes exclusivos.  
  
 O **dependências** guia contém os seguintes controles.  
  
 **Nome, origem e intervalo de versão**  
 Lista os elementos de dependência desse pacote, que são os outros pacotes que este pacote depende. Se um pacote de dependência for especificado, ele deve ser instalado antes que este pacote seja instalado; Caso contrário, esse pacote deve instalá-lo.  
  
 Pacotes de dependência são especificados pelo identificador, nome, intervalo de versão, fonte e como a dependência deve ser resolvido. Cada pacote de dependência é listada separadamente por nome, versão e código-fonte. Pacotes de dependência podem ser adicionados à lista, modificados e excluídos.  
  
 O identificador deve corresponder a `ID` atributo dos metadados de pacote de dependência. A origem pode ser um projeto na solução atual, uma extensão atualmente instalada ou um arquivo. O **como é resolvida de dependência** configuração pode ser o caminho relativo de um pacote aninhado ou a URL do local de download para a dependência. A identificação, a versão e a resolução do pacote dependência correspondem do `Id`, `Version`, e `Location` atributos de associado `Dependency` elemento.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 2.0 de extensão do VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
