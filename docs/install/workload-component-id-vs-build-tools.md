---
title: IDs de carga de trabalho e de componente das Ferramentas de Build do Visual Studio 2017 | Microsoft Docs
description: "Usar IDs de carga de trabalho e de componente do Visual Studio para criar aplicativos clássicos baseados no Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c8a3b886d32a2860a3b8acdd1cbb7d2830009dd4
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Diretório de componentes das Ferramentas de Build do Visual Studio 2017

As tabelas desta página listam as IDs que podem ser usadas para instalar o Visual Studio usando a linha de comando. Observe que adicionaremos outros componentes conforme atualizações forem liberadas para o Visual Studio.

Além disso, observe o seguinte sobre essa página:

* Cada carga de trabalho tem sua própria seção, seguida pela ID da carga de trabalho e por uma tabela dos componentes que estão disponíveis para a carga de trabalho.
* Por padrão, os componentes **Obrigatórios** serão instalados durante a instalação da carga de trabalho. Se preferir, também será possível instalar os componentes **Recomendados** e **Opcionais**.
* Também adicionamos uma seção que lista os componentes adicionais que não são afiliados a nenhuma carga de trabalho.

Para obter mais informações sobre como usar essas IDs, consulte a página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Além disso, para obter uma lista de IDs de carga de trabalho e de componente para outros produtos, consulte a página [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>Ferramentas do MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descrição:** fornece as ferramentas necessárias para criar aplicativos baseados em MSBuild.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.CoreBuildTools | Principais Ferramentas de Build do Visual Studio | 15.0.26228.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária


## <a name="visual-c-build-tools"></a>Ferramentas de build do Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Descrição:** criar aplicativos clássicos baseados no Windows usando o poder do conjunto de ferramentas do Visual C++, ATL e recursos opcionais como MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Principais recursos das Ferramentas de Build do Visual C++ | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.VC.CMake.Project | Ferramentas do Visual C++ para CMake | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ x86 e x64 | 15.0.26403.0 | Recomendado
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.ATL | Suporte ao Visual C++ ATL | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | Suporte ao MFC e ATL (x86 e x64) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.CLI.Support | Suporte ao C++/CLI | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos da Biblioteca Padrão | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK do Windows 10 (10.0.10240.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK do Windows 10 (10.0.14393.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK do Windows 8.1 e SDK do UCRT | 15.0.26208.0 | Opcional


## <a name="web-development-build-tools"></a>Ferramentas de build de desenvolvimento para a Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descrição:** tarefas e destinos do MSBuild para a compilação de aplicativos Web.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Ferramentas de build de desenvolvimento para a Web | 15.0.26323.1 | Necessária


## <a name="unaffiliated-components"></a>Componentes não afiliados

Estes são os componentes que não são incluídos com nenhuma carga de trabalho, mas que podem ser selecionados como um componente individual.

ID do componente | Nome | Versão
--- | --- | ---
N/D | N/D | N/D


## <a name="see-also"></a>Consulte também

* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)

