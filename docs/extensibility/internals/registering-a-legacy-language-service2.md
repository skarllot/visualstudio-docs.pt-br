---
title: Registrando um Service2 de idioma herdado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
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
ms.openlocfilehash: 9eebaf1928781a4495cfcf4625d8064b9175d361
ms.lasthandoff: 02/22/2017

---
# <a name="registering-a-legacy-language-service"></a>Registrar um serviço de linguagem herdado
As seções a seguir fornecem listas de entradas do registro para o idioma de várias opções de serviço disponíveis em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Na lista abaixo das entradas do registro, *VS Reg raiz* é igual a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, onde *x. y* é o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] número de versão.  
  
## <a name="registry-entries-for-language-service-options"></a>Entradas do registro para as opções de serviço de linguagem  
 O *VS Reg raiz*\Languages\Language serviços\\*nome do idioma* chave pode conter os seguintes valores.  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ|*\<GUID >*|GUID do serviço de idioma.|  
|LangResID|REG_DWORD|0x0-0xffff|Cadeia de caracteres resource identifier (ResID) para o nome de texto localizado da linguagem.|  
|Pacote|REG_SZ|*\<GUID >*|GUID do VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Especifica se o **conclusão de instrução** opções no **opções** caixa de diálogo estão habilitados.|  
|ShowSmartIndent|REG_DWORD|0-1|Especifica se a opção de selecionar **inteligente** recuo a **opções** caixa de diálogo está habilitada.|  
|RequestStockColors|REG_DWORD|0-1|Especifica se personalizado ou cores padrão são usadas para colorir palavras-chave.|  
|ShowHotURLs|REG_DWORD|0-1|Especifica se o usuário pode clicar em URLs.|  
|URLs não ativas por padrão|REG_DWORD|0-1|Especifica a configuração inicial para o **Habilitar navegação de URL de clique único** opção o **opções** caixa de diálogo.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Especifica se o serviço de linguagem tem "inserir espaços" como sua opção de guia padrão.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Habilita ou desabilita o **barra de navegação** opção o **opções** caixa de diálogo que mostra ou oculta o **barra de navegação**.|  
|Somente a janela de código único|REG_DWORD|0-1|Habilita ou desabilita o **nova janela** choice no **janela** menu para um serviço de linguagem.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Habilita ou desabilita um **opções** configuração da caixa de diálogo para **ocultar membros avançados**.|  
|Suporte CF_HTML|REG_DWORD|0-1|Especifica se o editor permite que a cópia e colagem de dados HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Especifica se o **números de linha** opções no **opções** caixa de diálogo está habilitada para um serviço de linguagem.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Especifica se membros avançados, como campos particulares estão ocultos em listas de conclusão.|  
|ShowBraceCompletion|REG_DWORD|0-1|Especifica se o **chave conclusão** opção o **opções** caixa de diálogo está habilitada.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Entradas do registro para as opções de idiomas do depurador  
 O *VS Reg raiz*\Languages\Language serviços\\*nome do idioma*\Debugger idiomas\\*GUID*\ chave pode incluir os seguintes valores.  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ|texto|O valor padrão pode ser usado para o nome do idioma do documento. O nome dessa chave é uma GUID de um avaliador de expressão que tem uma entrada correspondente em * \<VS Reg raiz >*\AD7Metrics\Expression avaliador.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Entradas de registro para opções de ferramentas do Editor  
 Você pode adicionar chaves de registro na chave EditorToolsOptions para nós de propriedade e páginas de propriedade. Essas chaves e seus valores identificam as páginas de propriedade no **opções** caixa de diálogo (no **ferramentas** menu) que são usados para configurar o serviço de linguagem. No exemplo a seguir, *nome de página* é o nome de uma página de propriedades e *nome do nó* é o nome de um nó na árvore no **opções** caixa de diálogo. A página de entrada e a entrada de nó devem ser especificadas separadamente.  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ|ResID|O nome de exibição localizado dessa página de opção. O nome pode ser texto literal ou #`nnn`, onde `nnn` é uma ID de recurso de cadeia de caracteres na DLL do VSPackage especificado satélite.|  
|Pacote|REG_SZ|*GUID*|O GUID do VSPackage que implementa essa página de opções.|  
|Página|REG_SZ|*GUID*|O GUID da página de propriedades para solicitar do VSPackage chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Se essa entrada do registro não estiver presente, a chave do registro descreve um nó, não uma página.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Entradas de registro para opções de extensão de nome de arquivo  
 A entrada para a extensão de arquivo deve incluir o ponto à esquerda, por exemplo ".myext".  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ|*GUID*|GUID de serviço para o serviço de linguagem padrão para esse tipo de extensão de nome de arquivo.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Entradas de registro de opções do Editor  
 O *VS Reg raiz*\Editors chave pode conter os seguintes valores:  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ|""|Não utilizado; Você pode colocar seu nome aqui para obter a documentação.|  
|DefaultToolboxTab|REG_SZ|""|Nome da guia caixa de ferramentas para tornar o padrão quando o editor está ativo.|  
|DisplayName|REG_SZ|ResID|Nome para exibir o **abrir com** caixa de diálogo. O nome é a ID de recurso de cadeia de caracteres ou um nome no formato padrão.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Usado para o **abrir com** comando de menu. Se você não deseja listar o editor de texto padrão na lista de editores disponíveis para um tipo de arquivo específico, defina esse valor como 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Usado para qualquer serviço de linguagem que pode abrir um arquivo com suporte a página de código. Por exemplo, quando você abre um arquivo. txt usando o **abrir com** comando, são fornecidas opções para usar o editor de código fonte com e sem codificação.<br /><br /> É o GUID especificado no nome da subchave para a fábrica de editor de página de código; é o GUID vinculado especificado nesta entrada do registro específica para a fábrica de editor regular. A finalidade dessa entrada é que se o IDE não abrir um arquivo usando o editor padrão, o IDE irá tentar usar o editor de Avançar na lista. Este editor próxima não deve ser a fábrica do editor de página de código porque essa fábrica de editor é basicamente o mesmo que a fábrica de editor que falhou.|  
|Pacote|REG_SZ|*\<GUID >*|GUID VSPackage ResID do nome de exibição.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Entradas de registro para opções de modo de exibição lógico  
 O *VS Reg raiz*\Editors\\*Editor GUI >*\LogicalViews chave pode conter os seguintes valores.  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ||Não utilizado.|  
|*\<GUID >*|REG_SZ|""|Chave para os modos de exibição lógicos com suporte. Você pode ter quantos desses conforme necessário. O nome da entrada do registro que é importante, não o valor, que é sempre uma cadeia de caracteres vazia.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Entradas de registro para opções de extensão de Editor  
 O *VS Reg raiz*\Editors\\*Editor GUID*\Extensions chave pode conter os seguintes valores. A extensão de nome de arquivo não inclui o ponto à esquerda.  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|(Padrão)|REG_SZ||Não utilizado.|  
|*\<ext >*|REG_DWORD|0-0xffffffff.|Prioridade relativa de extensões. Se dois ou mais idiomas compartilham a mesma extensão, o idioma de prioridade mais alta será escolhido.|  
  
 Além disso, a seleção de padrão do usuário atual para um editor é armazenada em HKEY_Current_User\Software\Microsoft\VisualStudio\\*x. y*\Default editores\\*ext*. É o GUID do serviço de idioma selecionado na entrada personalizada. Isso tem precedência para o usuário atual.  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entradas de registro para opções de serviço de idioma do pacote gerenciado Framework  
 As entradas de registro a seguir são específicas para as classes de serviço de linguagem do pacote gerenciado framework (MPF). Essas entradas do registro indicam suporte no serviço de linguagem para vários recursos do IntelliSense e outros recursos de edição avançados.  
  
 Essas entradas do registro são acessadas por meio de <xref:Microsoft.VisualStudio.Package.LanguagePreferences>classe.</xref:Microsoft.VisualStudio.Package.LanguagePreferences>  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Suporte para operações de IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Suporte a correspondência de pares de idiomas, como colchetes, parênteses e colchetes.|  
|Informaçãorápida|REG_DWORD|0-1|Suporte para a operação de informações rápidas do IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Suporte à exibição de par de idioma correspondente na barra de status.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Suporte à exibição pares correspondentes de linguagem, normalmente por meio de realce os dois elementos.|  
|MaxErrorMessages|REG_DWORD|0-n|O número máximo de erros que podem ser exibidos no **Error List** janela.|  
|CodeSenseDelay|REG_DWORD|0-n|O número de milissegundos de espera antes de iniciar qualquer plano de fundo de análise para uma operação de IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Suporte para análise em segundo plano.|  
|EnableCommenting|REG_DWORD|0-1|Suporte para comentar blocos de texto selecionados e também implica o suporte para o texto selecionado removendo.|  
|EnableFormatSelection|REG_DWORD|0-1|Suporte para formatação de texto, como o recuo automático ou ajustar a posição de chaves.|  
|AutoOutlining|REG_DWORD|0-1|Suporte para a estrutura de tópicos (regiões que podem ser recolhidos).|  
|MaxRegions|REG_DWORD|0-n|O número máximo de regiões ocultas por arquivo.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
