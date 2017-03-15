---
title: "O processo de transformação do modelo de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 30
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
ms.openlocfilehash: 673a97120148a77d12d19c7836683ce2d42a0f7f
ms.lasthandoff: 02/22/2017

---
# <a name="the-text-template-transformation-process"></a>O processo de transformação de modelo de texto
O processo de transformação do modelo de texto usa um arquivo de modelo de texto como entrada e gera um novo arquivo de texto como a saída. Por exemplo, você pode usar modelos de texto para gerar o código do Visual Basic ou c#, ou você pode gerar um relatório HTML.  
  
 Três componentes fazem parte desse processo: o mecanismo, o host e os processadores de diretriz. O mecanismo controla o processo. ele interage com o host e o processador de diretriz para produzir o arquivo de saída. O host fornece qualquer interação com o ambiente, como localizar arquivos e assemblies. O processador de diretriz adiciona funcionalidade, como ler dados de um arquivo XML ou um banco de dados.  
  
 O processo de transformação do modelo de texto é executado em duas etapas. Primeiro, o mecanismo cria uma classe temporária, que é conhecida como a classe de transformação gerada. Essa classe contém o código que é gerado pelas diretivas e blocos de controle. Depois disso, o mecanismo compila e executa a classe de transformação gerada para produzir o arquivo de saída.  
  
## <a name="components"></a>Componentes  
  
|Componente|Descrição|Personalizável (Sim/não)|  
|---------------|-----------------|------------------------------|  
|Mecanismo|O componente de mecanismo controla o processo de transformação do modelo de texto|Nº|  
|Host|O host é a interface entre o mecanismo e o ambiente do usuário. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]é um host do processo de transformação de texto.|Sim. Você pode escrever um host personalizado.|  
|Processadores de diretriz|Processadores de diretriz são classes que lidam com diretivas em modelos de texto. Você pode usar diretivas para fornecer dados a um modelo de texto de uma fonte de entrada.|Sim. Você pode escrever processadores de diretivas personalizadas|  
  
## <a name="the-engine"></a>O mecanismo  
 O mecanismo recebe o modelo como uma cadeia de caracteres do host, que lida com todos os arquivos que são usados no processo de transformação. O mecanismo solicita que o host para localizar qualquer processadores de diretivas personalizadas e outros aspectos do ambiente. O mecanismo, em seguida, compila e executa a classe de transformação gerada. O mecanismo retorna o texto gerado para o host, que normalmente salva o texto em um arquivo.  
  
## <a name="the-host"></a>O Host  
 O host é responsável por qualquer coisa relacionada ao ambiente de fora do processo de transformação, incluindo o seguinte:  
  
-   Localizando texto e arquivos binários solicitados pelo mecanismo de ou um processador de diretriz. O host pode pesquisar diretórios e cache de assembly global para localizar assemblies. O host pode localizar o código de processador de diretriz personalizado para o mecanismo. O host também pode localizar e ler arquivos de texto e retornar seu conteúdo como cadeias de caracteres.  
  
-   Fornece listas de assemblies padrão e namespaces que são usados pelo mecanismo para criar a classe de transformação gerada.  
  
-   Fornecendo o domínio de aplicativo que é usado quando o mecanismo compila e executa a classe de transformação gerada. Um domínio de aplicativo separado é usado para proteger o aplicativo host de erros no código do modelo.  
  
-   Gravar o arquivo de saída gerada.  
  
-   Definir a extensão padrão para o arquivo de saída gerada.  
  
-   Tratamento de erros de transformação do modelo de texto. Por exemplo, o host pode exibir os erros na interface do usuário ou gravá-los em um arquivo. (No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], erros são exibidos na janela de mensagem de erro.)  
  
-   Se um usuário chamou uma diretiva sem fornecer um valor, fornecendo um valor de parâmetro necessário. O processador de diretriz pode especificar o nome da diretiva e o parâmetro e pergunte o host para fornecer um valor padrão se ele tiver um.  
  
## <a name="directives-and-directive-processors"></a>Diretivas e processadores de diretriz  
 Uma diretiva é um comando no modelo de texto. Ele fornece parâmetros para o processo de geração. Normalmente diretivas definem a origem e o tipo do modelo ou outra entrada e a extensão de nome de arquivo do arquivo de saída.  
  
 Um processador de diretriz pode processar uma ou mais diretivas. Quando você transformar um modelo, você deve ter instalado um processador de diretriz que pode lidar com as diretivas em seu modelo.  
  
 Diretivas funcionam adicionando código na classe de transformação gerada. Você pode chamar diretivas de um modelo de texto e os processos de mecanismo todas as chamadas de diretiva quando ele cria a classe de transformação gerada. Depois de chamar uma diretiva com êxito, o restante do código que você escreve em seu modelo de texto pode contar com a funcionalidade que a diretiva fornece. Por exemplo, você pode fazer a chamada seguinte para o `import` diretiva no modelo:  
  
 `<#@ import namespace="System.Text" #>`  
  
 O processador de diretriz padrão converte isso para um `using` instrução na classe de transformação gerada. Você pode usar o `StringBuilder` classe no restante do seu código de modelo sem qualificá-lo como `System.Text.StringBuilder`.
