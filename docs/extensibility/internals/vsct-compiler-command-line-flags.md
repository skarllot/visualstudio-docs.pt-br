---
title: Sinalizadores de linha de comando do compilador VSCT | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
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
ms.openlocfilehash: 7839b5eae75ef5701d272c8b49a13172df6feb15
ms.lasthandoff: 02/22/2017

---
# <a name="vsct-compiler-command-line-flags"></a>Sinalizadores de linha de comando do compilador VSCT
O compilador de tabela de comando do Visual Studio (VSCT) fornece opções de linha de comando para garantir que a compilação bem-sucedida de arquivos. VSCT.  
  
## <a name="command-line-parameters"></a>Parâmetros de linha de comando  
 Para exibir a Ajuda básica de VSCT de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** janela, navegue até o *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Tools\Bin\ pasta e digite:  
  
```  
vsct /?  
```  
  
 Isso retorna:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Os caracteres - (traço) e / (barra) são ambas as notação aceitos para indicar os parâmetros de linha de comando.  
  
 Sinalizadores aceitáveis e seus significados são os seguintes.  
  
|Alternar|Descrição|  
|------------|-----------------|  
|-D|Especifique quaisquer símbolos definidos adicionais.|  
|-I|Indica que caminhos que devem ser usados para resolver referências de arquivo de inclusão adicionais.|  
|-L|Especifique o <xref:System.Globalization.CultureInfo>nome de cultura, como "en-US".</xref:System.Globalization.CultureInfo>|  
|-E|Emitir objetos c# no namespace especificado para itens de comando, seguido por [C | H | N]:*filename*onde C = C# H = cabeçalho de C++, N = namespace. O namespace é necessário para c#.|  
|-v|Saída detalhada.|  
  
 A opção -L Instrui o compilador para selecionar um grupo de sequências de caracteres para produzir o arquivo binário .cto que corresponde à determinado <xref:System.Globalization.CultureInfo>nome da cultura.</xref:System.Globalization.CultureInfo> O nome da cultura especificada deve corresponder o atributo de idioma de um ou mais [cadeias de caracteres elemento](../../extensibility/strings-element.md) no arquivo. VSCT. Se um elemento de cadeias de caracteres não tem nenhum atributo de idioma, ela é herdada do recipiente [CommandTable elemento](../../extensibility/commandtable-element.md).  
  
 Um arquivo. VSCT pode ter vários elementos de cadeias de caracteres, e cada um pode ter um atributo de idioma diferente. Globalização é obtida ao executar o compilador VSCT várias vezes e alterar o -L switch para cada nome de cultura.  
  
 Se o nome de cultura dado pela opção -L não coincide com o atributo de idioma de qualquer elemento de cadeias de caracteres, o compilador tenta corresponder o idioma e não a região. Por exemplo, se "en-US" não podem ser encontrado, o compilador tentará "en" em vez disso. Caso de falha, ele tentará a cultura atual do sistema operacional. Caso de falha, ele irá compilar o primeiro elemento de cadeias de caracteres que encontrar.  
  
 A opção -E pode ser usada para emitir um arquivo de cabeçalho do estilo C que contém os símbolos que são usados pela tabela de comando ou para emitir um arquivo em c# que contém objetos de símbolos de comando.  
  
 -D e – switches possuem a sintaxe dos sinalizadores pré-processador C Cl.exe que têm o mesmo nome. – D definições que têm o formato X = Y são usadas para a expansão do baseado em XML \<definidas > testes em `Condition` atributos. – Que incluem caminhos são usados para resolver \<incluir >, \<Extern > e \<Bitmap > referências de arquivo. Para obter mais informações, consulte o [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 O compilador VSCT também pode descompilar um arquivo binário compilado anteriormente. Para fazer isso, forneça um arquivo binário para o \<infile >.   Se o arquivo binário foi produzido pelo compilador VSCT, ele terá seus símbolos já inseridos e produzirá a saída com os nomes simbólicos em um \<símbolos > seção da saída. Se o binário foi produzido pelo compilador CTC, a saída conterá os GUIDs e IDs real. Se o arquivo de *.ctsym que é produzido por versões atuais do Ctc.exe estiver na mesma pasta que o arquivo de entrada binário, os símbolos serão carregados do arquivo e usados para a saída.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
