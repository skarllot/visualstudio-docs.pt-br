---
title: "Exemplos de parâmetros de linha de comando para a instalação do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
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
translationtype: Human Translation
ms.sourcegitcommit: 4e33dc3ebb32569b547aa9bcb6db9a15dbe4fc21
ms.openlocfilehash: ff67313f350264b39151bc0e2f7191ab16300f24
ms.lasthandoff: 04/05/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Exemplos de parâmetros de linha de comando para a instalação do Visual Studio 2017
Para ilustrar como [usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md), aqui estão vários exemplos que podem ser personalizados para atender às suas necessidades.

Em cada exemplo, `vs_enterprise.exe`, `vs_professional.exe` e `vs_community.exe` representam a respectiva edição do bootstrapper do Visual Studio, que é o arquivo pequeno (aproximadamente 1 MB) que inicia o processo de download. Se você estiver usando uma edição diferente, substitua o nome do bootstrapper adequado.

> [!NOTE]
> Todos os comandos exigem elevação administrativa e um prompt do Controle de Conta de Usuário será exibido se o processo não for iniciado em um prompt elevado.

* Instale uma instância mínima do Visual Studio, com nenhum prompt interativo, com exceção do progresso, exibido:
```cmd
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Instale silenciosamente, uma instância da área de trabalho do Visual Studio com o pacote de idioma francês, retornando somente quando o produto estiver instalado.
```cmd
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --quiet --wait
```

  > [!NOTE]
  >  O parâmetro `--wait` é projetado para uso em um arquivo em lotes. Em um arquivo em lotes, a execução do próximo comando não continuará até que a instalação seja concluída. A variável de ambiente `%ERRORLEVEL%` contém o valor retornado do comando, conforme documentado na página [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Baixe as cargas de trabalho do .NET desktop e do .NET web juntamente com todos os componentes recomendados e com a extensão do GitHub. Inclua apenas o pacote de idiomas em inglês:
```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Microsoft.Net.ComponentGroup.TargetingPacks.Common ^
   --add Microsoft.ComponentGroup.Blend ^
   --add Microsoft.VisualStudio.Component.EntityFramework ^
   --add Microsoft.VisualStudio.Component.DiagnosticTools ^
   --add Microsoft.VisualStudio.Component.DockerTools ^
   --add Microsoft.VisualStudio.Component.CloudExplorer ^
   --add Microsoft.VisualStudio.Component.Wcf.Tooling ^
   --add Component.GitHub.VisualStudio
```

   >[!NOTE]
   A Enterprise edition contém componentes recomendados adicionais, além daqueles incluídos aqui. Consulte o [diretório de componentes do Visual Studio Enterprise de 2017](workload-component-id-vs-enterprise.md) para obter uma lista de todos os componentes recomendados disponíveis no Visual Studio Enterprise.

* Inicie uma instalação interativa de todas as cargas de trabalho e componentes que estão disponíveis no Visual Studio 2017 Enterprise edition:
```cmd
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Instale uma segunda instância nomeada do Visual Studio 2017 Professional em um computador com Visual Studio 2017 Community edition já instalado, com suporte para o desenvolvimento do Node.js:
```cmd
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --nickname VSforNode
```

* Remova o componente Ferramentas de Criação de Perfil da instância do Visual Studio instalada por padrão:
```cmd
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

  > [!NOTE]
  >  Você pode usar o caractere `^` no final de uma linha de comando para concatenar várias linhas em um único comando. Como alternativa, é possível simplesmente colocar essas linhas juntas em uma única linha.

## <a name="see-also"></a>Consulte também

 * [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Criar uma instalação offline do Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

