---
title: Implantando um processador de diretriz personalizado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 783d7b517d551b530b0aba697c5f86da9bb37ad8
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-a-custom-directive-processor"></a>Implantando um processador de diretiva personalizada
Para usar um processador de diretriz personalizado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em qualquer computador, é necessário registrá-lo por um dos métodos descritos neste tópico.  
  
 Os métodos alternativos são:  
  
-   [Extensão do Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832). Isso fornece uma maneira de instalar e desinstalar o processador de diretriz em seu próprio computador e em outros computadores. Normalmente, você pode empacotar outros recursos na mesma VSIX.  
  
-   [VSPackage](../extensibility/internals/vspackages.md). Se você estiver for definir um VSPackage que contém outros recursos além do processador de diretriz, há um método conveniente para registrar o processador de diretriz.  
  
-   Definir uma chave do Registro. Nesse método, você adiciona uma entrada de Registro para o processador de diretriz.  
  
 Você precisará usar um desses métodos somente se quiser transformar o modelo de texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Se você usar um host personalizado em seu próprio aplicativo, seu host personalizado será responsável por localizar os processadores de diretrizes para cada diretiva.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>Implantando um processador de diretriz em uma VSIX  
 Você pode adicionar um processador de diretriz personalizado para um [extensão do Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Você precisará certificar-se de que os dois seguintes itens estejam contidos no arquivo .vsix:  
  
-   O assembly (.dll) que contém a classe do processador de diretriz personalizado.  
  
-   Um arquivo .pkgdef que registra o processador de diretriz. O nome raiz do arquivo deve ser igual ao do assembly. Por exemplo, seus arquivos podem ser nomeados como CDP.dll e CDP.pkgdef.  
  
 Para inspecionar ou alterar o conteúdo de um arquivo .vsix, altere a extensão do seu nome de arquivo para .zip e abra-o. Depois de editar o conteúdo, altere o nome do arquivo de volta para .vsix.  
  
 Há várias maneiras de criar um arquivo .vsix. O procedimento a seguir descreve um método.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Para desenvolver um processador de diretriz personalizado em um projeto VSIX  
  
1.  Crie um projeto VSIX no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   No **novo projeto** caixa de diálogo caixa, expanda **Visual Basic** ou **Visual C#**, em seguida, expanda **extensibilidade**. Clique em **projeto VSIX**.  
  
2.  Em **source.extension.vsixmanifest**, defina o tipo de conteúdo e edições com suporte.  
  
    1.  No VSIX manifesto do editor, sobre o **ativos** guia, escolha **novo** e defina as propriedades do novo item:  
  
         **Tipo de conteúdo** = **VSPackage**  
  
         **Projeto de origem** = \<*o projeto atual*>  
  
    2.  Clique em **edições selecionadas** e verifique os tipos de instalação no qual você deseja que o processador de diretriz para ser usado.  
  
3.  Adicione um arquivo .pkgdef e defina suas propriedades para ser incluídas no VSIX.  
  
    1.  Crie um arquivo de texto e nomeie- \< *assemblyName*> pkgdef.  
  
         \<*assemblyName*> geralmente é igual ao nome do projeto.  
  
    2.  Selecione-o no Gerenciador de Soluções e defina suas propriedades da seguinte maneira:  
  
         **Ação de compilação** = **conteúdo**  
  
         **Copiar para diretório de saída** = **copiar sempre**  
  
         **Incluir na VSIX** = **True**  
  
    3.  Defina o nome da VSIX e verifique se a ID é exclusiva.  
  
4.  Adicione o seguinte texto ao arquivo .pkgdef.  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Substitua os seguintes nomes pelos seus próprios nomes: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  Adicione as seguintes referências ao projeto:  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost. \*.0**  
  
6.  Adicione sua classe de processador de diretriz personalizado ao projeto.  
  
     Essa é uma classe pública que deve implementar <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.</xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> </xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>  
  
#### <a name="to-install-the-custom-directive-processor"></a>Para instalar o Processador de Diretriz Personalizado  
  
1.  No Windows Explorer (Explorador de Arquivos no Windows 8), abra o diretório de compilação (geralmente bin\Debug ou bin\Release).  
  
2.  Se você desejar instalar o processador de diretriz em outro computador, copie o arquivo .vsix para o outro computador.  
  
3.  Clique duas vezes no arquivo .vsix. O Instalador de Extensão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é exibido.  
  
4.  Reinicie o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Agora você poderá executar os modelos de texto que contêm diretivas que se referem ao processador de diretriz personalizado. Cada diretiva tem este formato:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Para desinstalar ou desabilitar temporariamente o processador de diretriz personalizado  
  
1.  No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **ferramentas** menu, clique em **Extension Manager**.  
  
2.  Selecione a VSIX que contém o processador de diretriz e, em seguida, clique em **desinstalar** ou **desabilitar**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Solução de problemas de um processador de diretriz em uma VSIX  
 Se o processador de diretriz não funcionar, as sugestões a seguir podem ajudar:  
  
-   O nome do processador que você especifica na diretiva personalizada deve corresponder ao `CustomDirectiveProcessorName` que você especificou no arquivo .pkgdef.  
  
-   O método `IsDirectiveSupported` deve retornar `true` quando o nome de seu `CustomDirective` é aprovado.  
  
-   Se você não conseguir ver a extensão no Gerenciador de extensão, mas o sistema não permitirá que você instalá-lo, exclua a extensão de **%localappdata%\Microsoft\VisualStudio\\\*.&0;\Extensions\\**.  
  
-   Abra o arquivo .vsix e inspecione seu conteúdo. Para abri-lo, altere a extensão do nome do arquivo para .zip. Verifique se contém os arquivos .dll, .pkgdef e extension.vsixmanifest. O arquivo extension.vsixmanifest deve conter a lista apropriada no nó SupportedProducts e deve conter também um nó VsPackage, sob o nó Conteúdo:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Implantando um processador de diretriz em um VSPackage  
 Se o processador de diretriz fizer parte de um VSPackage que será instalado no GAC, é possível fazer com que o sistema gere o arquivo .pkgdef para você.  
  
 Coloque o seguinte atributo na classe do pacote:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Esse atributo é colocado na classe de pacote, e não na classe de processador de diretriz.  
  
 O arquivo .pkgdef será gerado quando você compilar o projeto. Quando você instala o VSPackage, o arquivo .pkgdef registra o processador de diretriz.  
  
 Verifique se o arquivo .pkgdef aparece na pasta de compilação, que é geralmente bin\Debug ou bin\Release. Se não for exibido, abra o arquivo .csproj em um editor de texto e remova o seguinte nó: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Para obter mais informações, consulte [VSPackages](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Configuração de uma chave do Registro  
 Esse método de instalação de um processador de diretriz personalizado é o menos preferido. Não fornece uma maneira conveniente de habilitar e desabilitar o processador de diretriz, e não fornece um método de distribuição do processador de diretriz para outros usuários.  
  
> [!CAUTION]
>  A edição incorreta do registro pode danificar gravemente o sistema. Antes de alterar o Registro, faça o backup de todos os dados importantes no computador.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Para registrar um processador de diretriz definindo uma chave do Registro  
  
1.  Execute `regedit`.  
  
2.  Em regedit, navegue até  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
     Se você desejar instalar o processador de diretriz na versão de avaliação do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], insira “Exp” após “11.0”.  
  
3.  Adicione uma chave do Registro que tenha o mesmo nome da classe do processador de diretriz.  
  
    -   Na árvore do registro, clique com botão direito do **DirectiveProcessors** nó, aponte para **novo**e, em seguida, clique em **chave**.  
  
4.  No novo nó, adicione valores de cadeia de caracteres para Class e CodeBase ou Assembly, de acordo com as tabelas a seguir.  
  
    1.  Clique com botão direito no nó que você criou, aponte para **novo**e, em seguida, clique em **valor de cadeia de caracteres**.  
  
    2.  Edite o nome do valor.  
  
    3.  Clique duas vezes no nome e edite os dados.  
  
 Se o processador de diretriz personalizado não estiver no GAC, as subchaves do Registro deverão se parecer como na tabela a seguir:  
  
|Nome|Tipo|Dados|  
|----------|----------|----------|  
|(Padrão)|REG_SZ|(valor não definido)|  
|Classe|REG_SZ|**\<Nome do Namespace >. \<Nome da classe >**|  
|CodeBase|REG_SZ|**\<O caminho >\\<Your assembly=""></Your>\>**|  
  
 Se o assembly estiver no GAC, as subchaves do Registro deverão se parecer como na tabela a seguir:  
  
|Nome|Tipo|Dados|  
|----------|----------|----------|  
|(Padrão)|REG_SZ|(valor não definido)|  
|Classe|REG_SZ|\<**O nome de classe totalmente qualificado**>|  
|Assembly|REG_SZ|\<**O nome do Assembly no GAC**>|  
  
## <a name="see-also"></a>Consulte também  
 [Criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md)
