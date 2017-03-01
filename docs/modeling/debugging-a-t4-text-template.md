---
title: Depurando um modelo de texto T4 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 28
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
ms.openlocfilehash: 5b6cb4a83e6aa06f6b29987893232d8b6e203c56
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-a-t4-text-template"></a>Depurando um modelo de texto T4
Você pode definir pontos de interrupção em modelos de texto. Para depurar um modelo de texto de tempo de design, salve o arquivo de modelo de texto e, em seguida, escolha **depurar modelo T4** no menu de atalho do arquivo no Solution Explorer. Para depurar um modelo de texto de tempo de execução, simplesmente depure o aplicativo ao qual ele pertence.  
  
 Para depurar um modelo de texto, você deve compreender as etapas do processo de transformação do modelo. Diferentes tipos de erro podem ocorrer em cada etapa. As etapas são as seguintes.  
  
|Etapa|Modelo de tempo de design: quando isso ocorre|Modelo de tempo de execução: quando isso ocorre|  
|----------|--------------------------------------------|-----------------------------------------|  
|Código é gerado a partir do modelo de texto.<br /><br /> Erros em diretivas, ou incompatíveis ou fora de ordem `<#…#>` marcas.|Quando você salva o modelo ou invocar a transformação de texto.|Quando você salva o modelo ou invocar a transformação de texto.|  
|O código gerado é compilado.<br /><br /> Erros de compilação em seu código de modelo.|Imediatamente após a etapa anterior.|Juntamente com o código do aplicativo.|  
|O código é executado.<br /><br /> Erros de tempo de execução em seu código de modelo.|Imediatamente após a etapa anterior.|Quando seu aplicativo é executado e invoca o código do modelo.|  
  
 Na maioria dos casos, os números de linha no código do modelo são fornecidos no relatório de erros. Quando o relatório de erros se refere a um nome de arquivo temporário, a causa comum é um colchete incompatível no código do modelo de texto.  
  
 Você pode definir pontos de interrupção em modelos de texto e depurar da maneira usual.  
  
## <a name="common-errors-and-fixes"></a>Erros comuns e as correções  
 A tabela a seguir lista os erros mais comuns e suas correções.  
  
|Mensagem de erro|Descrição|Solução|  
|-------------------|-----------------|--------------|  
|Falha ao carregar a classe base "{0}" a partir da qual a classe Transformation foi herdada.|Ocorre se você não encontrar a classe base especificada no `inherits` parâmetro em uma diretiva de modelo. A mensagem fornece o número da linha de diretiva do modelo.|Certifique-se de que a classe especificada existe e se o assembly que ele existe em está especificado em uma diretiva de assembly.|  
|Falha ao resolver o texto incluso do arquivo: {0}|Ocorre quando não é possível encontrar um modelo incluído. A mensagem fornece o nome do arquivo de inclusão solicitada.|Certifique-se de que o caminho do arquivo é relativo ao caminho do modelo original, ou que o arquivo está em um local que está registrado com o host ou que há um caminho completo para o arquivo.|  
|Erros foram gerados ao inicializar o objeto de transformação. A transformação não será executada.|Ocorre quando o 'Initialize ()' da classe de transformação falhou ou retornado falso.|O código na função Initialize () é proveniente da classe base de transformação especificada no \<#@template#> diretiva e de processadores de diretriz. O erro que causou a inicialização falha provavelmente está na lista de erros. Investigue o motivo da falha. Você pode examinar o código gerado real para Initialize (), seguindo os procedimentos para depurar um modelo.|  
|O assembly '{0}' para o processador de diretriz '\ {1 \' não foi concedido ao conjunto de permissões FullTrust. Somente os assemblies confiáveis são permitidos para fornecer processadores de diretriz. Esse processador de diretriz não será carregado.|Ocorre quando o sistema não concede permissões FullTrust para um assembly que contém um processador de diretriz. A mensagem fornece o nome do assembly e o nome do processador de diretriz.|Certifique-se de que você só usar assemblies confiáveis no computador local.|  
|O caminho '{0}' deve ser local neste computador ou parte de uma zona confiável.|Ocorre quando uma diretiva ou diretiva de assembly faz referência a um arquivo que não está no seu computador local ou na zona confiável da rede.|Certifique-se de que o diretório onde estão localizadas o diretiva ou diretivas de assembly está na zona confiável. Você pode adicionar um diretório de rede à zona confiável através do Internet Explorer.|  
|Vários erros de sintaxe, como "Inválido token ' catch'" ou "um namespace não contém membros diretamente"|Número excessivo de fechamento de chaves em seu código de modelo. O compilador é confuso com o código de geração de padrão.|Verifique o número de fechamento de chaves e colchetes dentro de delimitadores de código.|  
|Loops ou condicionais não compilado ou executado corretamente. Por exemplo: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Esse código sempre gera o valor de i. Somente "número é:" é condicional.|No c#, sempre use chaves ao redor de blocos de texto que são incorporados em instruções de controle.|Adicionar chaves: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"Expressão muito complexa" ao processar um modelo de tempo de design ou compilando um modelo de tempo de execução (pré-processado).<br /><br /> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]parar de funcionar durante a tentativa de inspecionar o código gerado por um modelo de tempo de execução.|Bloco de texto é muito longo. T4 converte os blocos de texto em uma expressão de concatenação de cadeia de caracteres, com uma cadeia de caracteres literal para cada linha do modelo. Blocos de texto muito longo podem overstep limites de tamanho do compilador.|Divida o bloco de texto longo com um bloco de expressão, como:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Correções e descrições de aviso  
 A tabela a seguir lista os avisos mais comuns com correções, se disponível.  
  
|Mensagem de aviso|Descrição|Solução|  
|---------------------|-----------------|--------------|  
|O carregamento do arquivo '{0}' retornou uma cadeia de caracteres nula ou vazia.|Ocorre se um arquivo de modelo de texto incluído está em branco. A mensagem fornece o nome do arquivo do arquivo incluído.|Remova a diretiva include ou certifique-se de que o arquivo tem algum conteúdo.|  
|Compilando transformação:|Precede essa cadeia de caracteres para todos os erros ou avisos quando ele compila a transformação de origem do compilador. Essa cadeia de caracteres significa que o compilador gerou um erro ou aviso.|Se você tiver um problema ao encontrar a DLL, você precisará fornecer o caminho completo ou um nome forte completo se a DLL está no GAC.|  
|O parâmetro '{0}' já existe na diretiva. O parâmetro duplicado será ignorado.|Ocorre quando um parâmetro é especificado mais de uma vez em uma diretiva. A mensagem fornece o nome do parâmetro e o número da linha da diretiva.|Remova a especificação do parâmetro duplicado.|  
|Ocorreu um erro ao carregar o arquivo de inclusão '{0}'. A diretiva de inclusão será ignorada.|Ocorre quando não é possível localizar um arquivo especificado em um `include` diretiva. A mensagem fornece o nome do arquivo e o número da linha da diretiva.|Certifique-se de que o arquivo de inclusão existe no mesmo diretório do arquivo de modelo de texto original ou em um dos diretórios de inclusão que são registrados com o host.|  
|Uma classe base inválida foi especificada para a classe de transformação. A classe base deve derivar de TextTransformation.|Ocorre quando o `inherits` parâmetro em uma diretiva de modelo especifica uma classe que não herda de `TextTransformation`. A mensagem fornece o número da linha de diretiva do modelo.|Especifique uma classe que deriva de `TextTransformation`.|  
|Uma cultura inválida foi especificada na diretriz 'template'. A cultura deve estar no formato "xx-XX". A cultura invariável será usada.|Ocorre quando o parâmetro de cultura em uma diretiva de modelo foi especificado incorretamente. A mensagem fornece o número da linha de diretiva do modelo.|Altere o parâmetro de cultura para uma cultura válida no formato "xx-XX".|  
|Um valor de depuração inválido '{0}' foi especificado na diretiva do modelo. O valor de depuração deve ser "true" ou "false". O padrão de "false" será usado.|Ocorre quando o `debug` parâmetro em uma diretiva de modelo foi especificado incorretamente. A mensagem fornece o número da linha de diretiva do modelo.|Defina o parâmetro de depuração como "true" ou "false".|  
|Um valor de HostSpecific inválido '{0}' foi especificado na diretiva do modelo. O valor de HostSpecific deve ser "true" ou "false". O padrão de "false" será usado.|Ocorre quando o parâmetro de host específico em um `template` diretiva foi especificada incorretamente. A mensagem fornece o número da linha de diretiva do modelo.|Defina o parâmetro de host específico como "true" ou "false".|  
|Um idioma inválido '{0}' foi especificado na diretriz 'template'. O idioma deve ser "C#" ou "VB". O valor padrão de "C#" será usado.|Ocorre quando um idioma sem suporte é especificado na `template` diretiva. Somente "C#" ou "VB" são permitidos (não diferencia maiusculas de minúsculas). A mensagem fornece o número da linha de diretiva do modelo.|Definir o `language` parâmetro na diretiva do modelo "C#" ou "VB".|  
|Várias diretrizes de saída foram encontradas no modelo. Tudo, exceto o primeiro deles será ignorado.|Ocorre quando várias `output` as diretivas são especificadas em um arquivo de modelo. A mensagem fornece o número da linha da diretiva de saída duplicado.|Remover duplicatas `output` diretivas.|  
|Foram encontradas várias diretivas de modelo no modelo. Tudo, exceto o primeiro deles será ignorado. Vários parâmetros para a diretiva de modelo devem ser especificados dentro de uma diretriz de modelo.|Ocorre se você especificar vários `template` diretivas dentro de um arquivo de modelo de texto (inclusive arquivos incluídos). A mensagem fornece o número da linha da diretiva modelo duplicado.|Agregar diferentes `template` diretivas em um `template` diretiva.|  
|Nenhum processador foi especificado para uma diretiva denominada '{0}'. A diretiva será ignorada.|Ocorre se você especificar um `custom` diretiva, mas não fornece um `processor` atributo. A mensagem fornece o nome da diretiva e o número da linha.|Forneça um `processor` atributo com o nome do `directive` processador para a diretiva.|  
|Não foi possível encontrar um processador chamado '{0}' na diretriz chamada '\ {1 \'. A diretiva será ignorada.|Ocorre quando o sistema não encontrou o `directive` processador especificado dentro de uma `custom` diretiva. A mensagem fornece o nome da diretiva, nome do processador e o número da linha da diretiva.|Definir o `processor` atributo na diretiva para o nome do processador de diretriz.|  
|Um parâmetro obrigatório '{0}' para a diretiva '\ {1 \' não foi encontrado. A diretiva será ignorada.|Ocorre quando o sistema não fornecer um parâmetro obrigatório de diretiva. A mensagem fornece o nome do parâmetro ausente, o nome da diretiva e o número da linha.|Forneça o parâmetro ausente.|  
|O processador chamado '{0}' não oferece suporte à diretriz chamada '\ {1 \'. A diretiva será ignorada.|Ocorre quando um processador de diretriz não dá suporte a uma diretiva. A mensagem fornece o nome e número da linha a diretiva ofensiva junto com o nome do processador de diretriz.|Corrija o nome da diretiva.|  
|A diretiva de inclusão de arquivo '{0}' causa um loop infinito.|Exibida se as diretivas de inclusão circular especificados (por exemplo, um arquivo inclui arquivos B, que inclui um arquivo).|Não especifique circular diretivas de inclusão.|  
|Executando transformação:|Precede essa cadeia de caracteres para todos os erros ou avisos que são gerados durante a execução da transformação.|Não aplicável.|  
|Uma marca de início ou fim inesperada foi encontrada dentro de um bloco. Certifique-se de que você não digitou incorretamente uma marca de início ou término e que não há blocos aninhados no modelo.|Exibida quando o inesperado \<# ou #>. Ou seja, se você tiver um \<# após outra marca aberta que não foram fechada, ou você tem um #> quando há uma marca aberta fechada antes dele. A mensagem fornece o número da linha da marca incompatível.|Remova a marca de início ou término incompatível, ou use um caractere de escape.|  
|Uma diretriz foi especificada em um formato incorreto. A diretiva será ignorada. Especifique a diretriz no formato`<#@ name [parametername="parametervalue"]*  #>`|Exibido pelo analisador se uma diretiva não for especificada no formato correto. A mensagem fornece o número da linha da diretiva incorreta.|Certifique-se de que todas as diretivas estão no formato `<#@ name [parametername="parametervalue"]*  #>`. Para obter mais informações, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).|  
|Falha ao carregar o Assembly '{0}' registrado do processador de diretriz '\ {1 \'<br /><br /> {2}|Ocorre quando um processador de diretriz não pôde ser carregado pelo host. A mensagem identifica o assembly fornecido para o processador de diretriz e o nome do processador de diretriz.|Certifique-se de que o processador de diretriz está registrado corretamente e se o assembly existe.|  
|Falha ao localizar o tipo '{0}' no Assembly '\ {1 \' registrado do processador de diretriz '2 \}'<br /><br /> {3}|Ocorre quando um tipo de processador de diretriz não pôde ser carregado no seu assembly. A mensagem fornece o nome do tipo, o assembly e o processador de diretriz.|O vshost Localiza informações do processador de diretriz (nome do assembly e tipo) no registro. Certifique-se de que o processador de diretriz está registrado corretamente e se o tipo existe no assembly.|  
|Ocorreu um problema ao carregar o assembly "{0}"|Ocorre quando há um problema ao carregar um assembly. A mensagem fornece o nome do assembly.|Você pode especificar os assemblies sejam carregados em \<@# assembly #> diretivas e por processadores de diretriz. A mensagem de erro que segue essa sequência de caracteres deve fornecer mais dados sobre por que o módulo falhou ao carregar.|  
|Houve um problema ao criar e inicializar o processador de uma diretriz chamada '\ {1 \'. O tipo do processador é {0}. A diretiva será ignorada.|Ocorre quando o sistema não conseguiu criar ou inicializar um processador de diretriz. A mensagem fornece o nome e número da linha a diretiva e o tipo do processador.|Certifique-se de usar o processador de diretriz correto e se o processador de diretriz tem um construtor padrão público. Caso contrário, use as opções de depuração para descobrir por que o método Initialize () do processador de diretriz está falhando. Para obter mais informações, consulte [modelos de solução de problemas de texto](../modeling/debugging-a-t4-text-template.md).|  
|Uma exceção foi lançada durante o processamento de uma diretriz chamada '{0}'.|Ocorre quando um processador de diretriz lança uma exceção ao processar uma diretiva.|Certifique-se de que os parâmetros para o processador de diretriz estão corretos.|  
|O host lançou uma exceção durante a tentativa de resolver a referência de assembly '{0}'.|Ocorre quando o host lança uma exceção ao tentar resolver uma referência de assembly. A mensagem fornece o assembly de referência da cadeia de caracteres.|Assembly referências vêm \<@# assembly #> diretivas e de processadores de diretriz. Certifique-se de que o parâmetro 'name' fornecido no parâmetro assembly está correto.|  
|Tente especificar o valor de \ {1 \ sem suporte '{0}' para diretiva \ {2 \|Ocorre por meio de RequiresProvidesDirectiveProcessor (todos os processadores de diretriz gerados derivam), ao fornecer um suporte requer ou fornece um argumento.|Certifique-se de que os nomes em name = 'value' pares fornecidas a requer e fornece parâmetros estão corretos.|
