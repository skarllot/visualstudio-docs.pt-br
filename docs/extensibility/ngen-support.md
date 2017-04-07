---
title: Suporte a NGen no VSIX v3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>Suporte a NGen no VSIX v3

Com o Visual Studio 2017 e o novo v3 VSIX extensão (versão 3) manifesto formato, extensão os desenvolvedores podem agora "ngen" seus assemblies no momento da instalação.

Abaixo está um trecho do MSDN que explica quais "ngen":

>O Gerador de Imagem Nativa (Ngen.exe) é uma ferramenta que melhora o desempenho de aplicativos gerenciados. Ngen.exe cria imagens nativas, que são arquivos que contém o código de máquina específico do processamento compilado e as instala no cache de imagem nativa do computador local. O tempo de execução pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.
>
>de [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

"NGen" um assembly, VSIX deve ser instalado "por instância por máquina". Isso pode ser habilitado, marcando a caixa de seleção "todos os usuários" no designer de vsixmanifest:

![Verifique todos os usuários](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Como habilitar o Ngen

Para habilitar o ngen para um assembly, você pode usar o **propriedades** janela no Visual Studio.

Há 4 propriedades que podem ser definidas:

1. **NGen** (Boolean) – se for true, o instalador do Visual Studio será "ngen" do assembly.
2. **Aplicativo NGen** (cadeia de caracteres) – Ngen fornece a oportunidade de usar o arquivo App. config de um aplicativo para resolver as dependências do assembly. Esse valor deve ser definido para um aplicativo cujo App. config que você deseja usar (relativo ao diretório de instalação do Visual Studio).
3. **Arquitetura do NGen** (enum) – a arquitetura para compilar o assembly nativamente. As opções são: uma. B NotSpecified. X86 c. X64 d. Todos
4. **Prioridade do NGen** (número inteiro entre 1 e 3) – nível de prioridade do Ngen é documentada em [Ngen.exe níveis de prioridade](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Aqui está uma olhada a **propriedades** janela em ação:

![NGen em Propriedades](media/ngen-in-properties.png)

Isso irá adicionar metadados a referência do projeto dentro do arquivo do projeto VSIX. csproj:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Observação:** é possível editar o arquivo. csproj diretamente, se preferir.

## <a name="extra-information"></a>Informações adicionais

As alterações de propriedade designer se aplicam a mais do que apenas referências do projeto; Você pode definir os metadados do Ngen para itens dentro de seu projeto também, desde que os itens são assemblies .NET (usando os métodos descritos acima).
