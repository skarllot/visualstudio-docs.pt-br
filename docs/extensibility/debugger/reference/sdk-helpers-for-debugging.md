---
title: "Auxiliares do SDK para depuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
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
ms.openlocfilehash: 8978ddf94cf37d13d7e70e5503a4821415f10977
ms.lasthandoff: 02/22/2017

---
# <a name="sdk-helpers-for-debugging"></a>Auxiliares do SDK para depuração
Essas funções e as declarações são funções de auxiliar global para implementar mecanismos de depuração, avaliadores de expressão e provedores de símbolo em C++.  
  
> [!NOTE]
>  Há não gerenciados versões dessas funções e declarações neste momento.  
  
## <a name="overview"></a>Visão Geral  
 Em ordem para mecanismos de depuração, avaliadores de expressão e provedores de símbolo a ser usado pelo Visual Studio, eles devem ser registrados. Isso é feito definindo subchaves do registro e entradas, também conhecidas como "métricas de configuração". As seguintes funções globais são criadas para facilitar o processo de atualizar essas métricas. Consulte a seção sobre locais do registro para descobrir o layout de cada subchave do registro que é atualizado por essas funções.  
  
## <a name="general-metric-functions"></a>Funções de métrica geral  
 Essas são funções gerais usadas pelos mecanismos de depuração. Especializado funções de avaliadores de expressão e provedores de símbolo detalhados posteriormente.  
  
### <a name="getmetric-method"></a>Método GetMetric  
 Recupera um valor de métrica do registro.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszMachine|[in] Nome de uma máquina remota possivelmente cujo registro será gravado (`NULL` significa computador local).|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico, avaliador, exceção etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser obtido. Isso corresponde a um nome de valor específico.|  
|pdwValue|[in] O local de armazenamento do valor de métrica. Existem vários tipos de GetMetric que pode retornar uma matriz de GUIDs, BSTR, um GUID ou uma DWORD (como neste exemplo).|  
|pszAltRoot|[in] Uma raiz de registro alternativo para usar. Definido como `NULL` para usar o padrão.|  
  
### <a name="setmetric-method"></a>Método SetMetric  
 Define o valor da métrica especificado no registro.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico, avaliador, exceção etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser obtido. Isso corresponde a um nome de valor específico.|  
|dwValue|[in] O local de armazenamento do valor de métrica. Existem vários tipos de SetMetric que pode armazenar um DWORD (no exemplo), um BSTR, um GUID ou uma matriz de GUIDs.|  
|fUserSpecific|[in] TRUE se a métrica é específico do usuário e se ele deve ser escrito de hive do usuário em vez do hive do computador local.|  
|pszAltRoot|[in] Uma raiz de registro alternativo para usar. Definido como `NULL` para usar o padrão.|  
  
### <a name="removemetric-method"></a>Método RemoveMetric  
 Remove a métrica especificada do registro.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico, avaliador, exceção etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser removido. Isso corresponde a um nome de valor específico.|  
|pszAltRoot|[in] Uma raiz de registro alternativo para usar. Definido como `NULL` para usar o padrão.|  
  
### <a name="enummetricsections-method"></a>Método EnumMetricSections  
 Enumera as várias seções de métrica no registro.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszMachine|[in] Nome de uma máquina remota possivelmente cujo registro será gravado (`NULL` significa computador local).|  
|pszType|[in] Um dos tipos de métrica.|  
|rgguidSections|[no, out] Pré-alocados matriz de GUIDs para ser preenchido.|  
|pdwSize|[in] O número máximo de GUIDs que podem ser armazenados na `rgguidSections` matriz.|  
|pszAltRoot|[in] Uma raiz de registro alternativo para usar. Definido como `NULL` para usar o padrão.|  
  
## <a name="expression-evaluator-functions"></a>Funções do avaliador de expressão  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetEEMetric|Recupera um valor de métrica do registro.|  
|SetEEMetric|Define o valor da métrica especificado no registro.|  
|RemoveEEMetric|Remove a métrica especificada do registro.|  
|GetEEMetricFile|Obtém um nome de arquivo a métrica especificada e o carrega, retornando o conteúdo do arquivo como uma cadeia de caracteres.|  
  
## <a name="exception-functions"></a>Funções de exceção  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera um valor de métrica do registro.|  
|SetExceptionMetric|Define o valor da métrica especificado no registro.|  
|RemoveExceptionMetric|Remove a métrica especificada do registro.|  
|RemoveAllExceptionMetrics|Remove todas as métricas de exceção do registro.|  
  
## <a name="symbol-provider-functions"></a>Funções de símbolo do provedor  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetSPMetric|Recupera um valor de métrica do registro.|  
|SetSPMetric|Define o valor da métrica especificado no registro.|  
|RemoveSPMetric|Remove a métrica especificada do registro.|  
  
## <a name="enumeration-functions"></a>Funções de enumeração  
  
|Função|Descrição|  
|--------------|-----------------|  
|EnumMetricSections|Enumera todas as métricas para um tipo específico de métrica.|  
|EnumDebugEngine|Enumera os mecanismos de depuração registrado.|  
|EnumEEs|Enumera os avaliadores de expressão registrado.|  
|EnumExceptionMetrics|Enumera todas as métricas de exceção.|  
  
## <a name="metric-definitions"></a>Definições de métricas  
 Essas definições podem ser usadas para nomes de métrica predefinidos. Os nomes correspondem aos nomes de valor e várias chaves de registro e são definidos como cadeias de caracteres largos: por exemplo, `extern LPCWSTR metrictypeEngine`.  
  
|Tipos predefinidos de métricos|Descrição: A chave base para...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Todas as métricas do mecanismo de depuração.|  
|metrictypePortSupplier|Todas as métricas de fornecedor de porta.|  
|metrictypeException|Todas as métricas de exceção.|  
|metricttypeEEExtension|Todas as extensões do avaliador de expressão.|  
  
|Propriedades do mecanismo de depuração|Descrição|  
|-----------------------------|-----------------|  
|metricAddressBP|Defina como zero para indicar o suporte para pontos de interrupção de endereço.|  
|metricAlwaysLoadLocal|Defina como zero para sempre carregar o mecanismo de depuração localmente.|  
|metricLoadInDebuggeeSession|NÃO USADO|  
|metricLoadedByDebuggee|Defina como zero para indicar que o mecanismo de depuração sempre será carregado com ou o programa que está sendo depurado.|  
|metricAttach|Defina como zero para indicar o suporte para conexão com os programas existentes.|  
|metricCallStackBP|Defina como zero para indicar o suporte para pontos de interrupção de pilha de chamada.|  
|metricConditionalBP|Defina como zero para indicar o suporte para a configuração de pontos de interrupção condicionais.|  
|metricDataBP|Defina como zero para indicar o suporte para a configuração dos pontos de interrupção em alterações nos dados.|  
|metricDisassembly|Defina como zero para indicar o suporte para a produção de uma listagem de desmontagem.|  
|metricDumpWriting|Defina como zero para indicar o suporte para despejo de gravação (o despejo de memória para um dispositivo de saída).|  
|metricENC|Defina como zero para indicar o suporte para editar e continuar. **Observação:** um mecanismo personalizado de depuração nunca deve definir isso ou sempre deverá defini-lo como 0.|  
|metricExceptions|Defina como zero para indicar o suporte para exceções.|  
|metricFunctionBP|Definido como zero para indicar o suporte para pontos de interrupção nomeados (pontos de interrupção falhar quando um determinado nome de função é chamado).|  
|metricHitCountBP|Defina como zero para indicar o suporte para a configuração dos pontos de interrupção "de acertos do ponto" (os pontos de interrupção são disparados somente após visitado um determinado número de vezes).|  
|metricJITDebug|Defina como zero para indicar o suporte de depuração just-in-time (o depurador é iniciado quando ocorre uma exceção em um processo em execução).|  
|metricMemory|NÃO USADO|  
|metricPortSupplier|Defina isso para o CLSID do fornecedor de porta, se uma estiver implementada.|  
|metricRegisters|NÃO USADO|  
|metricSetNextStatement|Defina como zero para indicar o suporte para definir a próxima instrução (que ignora a execução de instruções intermediárias).|  
|metricSuspendThread|Defina como zero para indicar o suporte para suspender a execução do thread.|  
|metricWarnIfNoSymbols|Defina como zero para indicar que o usuário será notificado se não houver nenhum símbolo.|  
|metricProgramProvider|Defina o CLSID do provedor do programa.|  
|metricAlwaysLoadProgramProviderLocal|Defina como zero para indicar que os do provedor de programa deve sempre ser carregado localmente.|  
|metricEngineCanWatchProcess|Defina como zero para indicar que o mecanismo de depuração irá observar para processar eventos em vez do provedor do programa.|  
|metricRemoteDebugging|Defina como zero para indicar o suporte para depuração remota.|  
|metricEncUseNativeBuilder|Defina como zero para indicar que o editar e continuar Manager devem usar encbuild.dll do mecanismo de depuração para criar para editar e continuar. **Observação:** um mecanismo personalizado de depuração nunca deve definir isso ou sempre deverá defini-lo como 0.|  
|metricLoadUnderWOW64|Defina-o como diferente de zero para indicar que o mecanismo de depuração deve ser carregado no processo a ser depurado em WOW durante a depuração de um processo de 64 bits. Caso contrário, o mecanismo de depuração será carregado no processo do Visual Studio (que é executado no WOW64).|  
|metricLoadProgramProviderUnderWOW64|Defina-o como diferente de zero para indicar que o provedor do programa deve ser carregado no processo a ser depurado durante a depuração de um processo de 64 bits em WOW; Caso contrário, ele será carregado no processo do Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Defina como zero para indicar que o processo deve ser interrompida se uma exceção não tratada é lançada limites gerenciados/código.|  
|metricAutoSelectPriority|Defina a prioridade para a seleção automática do mecanismo de depuração (mais altos valores igual a prioridade mais alta).|  
|metricAutoSelectIncompatibleList|Chave do registro que contém entradas que especificam as GUIDs para os mecanismos de depuração a ser ignorada na seleção automática. Essas entradas são um número (0, 1, 2 e assim por diante) com um GUID expressado como uma cadeia de caracteres.|  
|metricIncompatibleList|Chave do registro que contém entradas que especificam as GUIDs para os mecanismos de depuração que são incompatíveis com o mecanismo de depuração.|  
|metricDisableJITOptimization|Defina como zero para indicar que as otimizações just-in-time (para código gerenciado) devem ser desabilitadas durante a depuração.|  
  
|Propriedades do avaliador de expressão|Descrição|  
|-------------------------------------|-----------------|  
|metricEngine|Isso mantém o número de mecanismos de depuração que suportam o avaliador da expressão especificada.|  
|metricPreloadModules|Defina como zero para indicar que módulos devem ser pré-carregado quando um avaliador de expressão é iniciado em um programa.|  
|metricThisObjectName|Defina o nome do objeto "this".|  
  
|Propriedades de extensão do avaliador de expressão|Descrição|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nome da dll que oferece suporte a essa extensão.|  
|metricExtensionRegistersSupported|Lista de registros com suporte.|  
|metricExtensionRegistersEntryPoint|Ponto de entrada para acessar registros.|  
|metricExtensionTypesSupported|Lista de tipos com suporte.|  
|metricExtensionTypesEntryPoint|Ponto de entrada para acessar tipos.|  
  
|Propriedades da porta de fornecedor|Descrição|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|O CLSID do seletor de porta (uma caixa de diálogo, o usuário pode usar para selecionar portas e adicionar portas a serem usadas para depuração).|  
|metricDisallowUserEnteredPorts|Diferente de zero se as portas de entrada do usuário não podem ser adicionadas ao fornecedor porta (Isso torna a caixa de diálogo Seletor de porta essencialmente somente leitura).|  
|metricPidBase|A ID de processo base usada pelo fornecedor de porta ao alocar identificadores de processo.|  
  
|Tipos de armazenamento de SP predefinidos|Descrição|  
|-------------------------------|-----------------|  
|storetypeFile|Os símbolos são armazenados em um arquivo separado.|  
|storetypeMetadata|Os símbolos são armazenados como metadados em um assembly.|  
  
|Propriedades variadas|Descrição|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Defina isso para mostrar o código nonuser diferente de zero.|  
|metricJustMyCodeStepping|Defina como zero para indicar que a revisão pode ocorrer somente no código do usuário.|  
|metricCLSID|CLSID para um objeto de um tipo específico de métrica.|  
|metricName|Nome amigável de um objeto de um tipo específico de métrica.|  
|metricLanguage|Nome do idioma.|  
  
## <a name="registry-locations"></a>Locais do registro  
 As métricas são ler e gravadas no registro, especificamente ao `VisualStudio` subchave.  
  
> [!NOTE]
>  Na maioria das vezes, as métricas serão gravadas na chave HKEY_LOCAL_MACHINE. No entanto, às vezes, HKEY_CURRENT_USER será a chave de destino. Dbgmetric.lib manipula as duas chaves. Ao obter uma métrica, ele procura HKEY_CURRENT_USER e, depois, HKEY_LOCAL_MACHINE. Quando ele é definir uma métrica, um parâmetro especifica qual chave de nível superior para usar.  
  
 *[chave]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[raiz versão]*\  
  
 *[raiz métrica]*\  
  
 *[tipo de métrica]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[chave]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|  
|*[raiz versão]*|A versão do Visual Studio (por exemplo, `7.0`, `7.1`, ou `8.0`). No entanto, essa raiz também pode ser modificada usando o **/rootsuffix** alternar para **devenv.exe**. VSIP, esse modificador normalmente é **Exp**, portanto, a raiz de versão deve ser, por exemplo, 8.0Exp.|  
|*[raiz métrica]*|Isso é `AD7Metrics` ou `AD7Metrics(Debug)`, dependendo se a versão de depuração de dbgmetric.lib é usada. **Observação:** se dbgmetric.lib for usado, ou não essa convenção de nomenclatura deverão ser seguida se houver diferenças entre debug e release versões que deverá ser refletidas no registro.|  
|*[tipo de métrica]*|O tipo de métrica a ser gravado: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etc. Estes são definidos como dbgmetric.h como `metricTypeXXXX`, onde `XXXX` é o nome do tipo específico.|  
|*[métrica]*|O nome de uma entrada a ser atribuído um valor para definir a métrica. A organização real das métricas depende do tipo de métrica.|  
|*[valor de métrica]*|O valor atribuído para a métrica. O tipo que de valor deve ter (string), números, etc. depende a métrica.|  
  
> [!NOTE]
>  Todos os GUIDs são armazenados no formato de `{GUID}`. Por exemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Os mecanismos de depuração  
 A seguir está a organização das métricas de mecanismos de depuração no registro. `Engine`é o nome do tipo de métrica para um mecanismo de depuração e corresponde à *[tipo de métrica]* na subárvore de registro acima.  
  
 `Engine`\  
  
 *[mecanismo guid]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `PortSupplier`\  
  
 `0` = *[guid do fornecedor de porta]*  
  
 `1` = *[guid do fornecedor de porta]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[mecanismo guid]*|O GUID do mecanismo de depuração.|  
|*[guid de classe]*|O GUID da classe que implementa esse mecanismo de depuração.|  
|*[guid do fornecedor de porta]*|O GUID do fornecedor de porta, se houver. Vários mecanismos de depuração usam o fornecedor de porta padrão e, portanto, não especifique seu próprio fornecedor. Nesse caso, a subchave `PortSupplier` estará ausente.|  
  
### <a name="port-suppliers"></a>Fornecedores de porta  
 A seguir está a organização das métricas de fornecedor de porta no registro. `PortSupplier`é o nome do tipo de métrica para um fornecedor de porta e corresponde à *[tipo de métrica]*.  
  
 `PortSupplier`\  
  
 *[guid do fornecedor de porta]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do fornecedor de porta]*|O GUID do fornecedor de porta|  
|*[guid de classe]*|O GUID da classe que implementa esse fornecedor de porta|  
  
### <a name="symbol-providers"></a>Provedores de símbolo  
 A seguir está a organização das métricas de fornecedor de símbolo no registro. `SymbolProvider`é o nome do tipo de métrica para o provedor de símbolo e corresponde à *[tipo de métrica]*.  
  
 `SymbolProvider`\  
  
 *[guid do provedor de símbolo]*\  
  
 `file`\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `metadata`\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do provedor de símbolo]*|O GUID do provedor de símbolo|  
|*[guid de classe]*|O GUID da classe que implementa esse provedor de símbolo|  
  
### <a name="expression-evaluators"></a>Avaliadores de expressão  
 A seguir está a organização das métricas de avaliador de expressão no registro. `ExpressionEvaluator`é o nome do tipo de métrica para o avaliador de expressão e corresponde à *[tipo de métrica]*.  
  
> [!NOTE]
>  O tipo de métrica para `ExpressionEvaluator` não é definida no dbgmetric.h, como presume-se que todas as alterações de métrica de avaliadores de expressão irão por meio das funções de métrica de avaliador de expressão apropriada (o layout do `ExpressionEvaluator` subchave é um pouco complicada, portanto, os detalhes estão ocultos dentro de dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[linguagem guid]*\  
  
 *[fornecedor guid]*\  
  
 `CLSID` = *[guid de classe]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `Engine`\  
  
 `0` = *[guid do mecanismo de depuração]*  
  
 `1` = *[guid do mecanismo de depuração]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[linguagem guid]*|O GUID de um idioma|  
|*[fornecedor guid]*|O GUID de um fornecedor|  
|*[guid de classe]*|O GUID da classe que implementa esse avaliador de expressão|  
|*[guid do mecanismo de depuração]*|O GUID de um mecanismo de depuração que este avaliador de expressão funciona com|  
  
### <a name="expression-evaluator-extensions"></a>Extensões do avaliador de expressão  
 A seguir está a organização das métricas de extensão do avaliador de expressão no registro. `EEExtensions`é o nome do tipo de métrica para a expressão de extensões do avaliador e corresponde à *[tipo de métrica]*.  
  
 `EEExtensions`\  
  
 *[extensão guid]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[extensão guid]*|O GUID de uma extensão do avaliador de expressão|  
  
### <a name="exceptions"></a>Exceções  
 A seguir está a organização das métricas de exceções no registro. `Exception`é o nome do tipo de métrica para as exceções e corresponde à *[tipo de métrica]*.  
  
 `Exception`\  
  
 *[guid do mecanismo de depuração]*\  
  
 *[tipos de exceção]*\  
  
 *[exceção]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[exceção]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do mecanismo de depuração]*|O GUID de um mecanismo de depuração que oferece suporte a exceções.|  
|*[tipos de exceção]*|Um título geral da subchave identifica a classe de exceções que podem ser manipulados. Nomes típicos são **exceções C++**, **exceções Win32**, **exceções do Common Language Runtime**, e **verificações de tempo de execução nativo**. Esses nomes também são usados para identificar uma determinada classe de exceção para o usuário.|  
|*[exceção]*|Um nome para uma exceção: por exemplo, **com_error** ou **Control-Break**. Esses nomes também são usados para identificar uma exceção em particular para o usuário.|  
  
## <a name="requirements"></a>Requisitos  
 Esses arquivos estão localizados na [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] diretório de instalação do SDK (por padrão, *[unidade]*\Program Files\Microsoft SDK do Visual Studio 2010\\).  
  
 Cabeçalho: includes\dbgmetric.h  
  
 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
