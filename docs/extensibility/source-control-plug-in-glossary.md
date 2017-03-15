---
title: "Glossário de plug-in de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
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
ms.openlocfilehash: 251e104336d19e9f88926e5ca75a85330039fbe8
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-glossary"></a>Glossário de plug-in de controle de origem
Os seguintes termos úteis e definições pertencem a documentação do SDK de plug-in de controle de origem.  
  
## <a name="definitions"></a>Definições  
 Check-in  
 Quando um usuário faz alterações em uma cópia de trabalho, um usuário deve enviar as alterações da cópia de trabalho para o repositório de controle de origem central. Isso cria uma nova revisão do arquivo que está disponível para outros usuários. Esse processo é chamado um check-in.  
  
 Fazer Check-out  
 O ato de solicitar uma cópia de trabalho do repositório, informando o repositório de sua intenção de modificá-lo. Uma cópia de trabalho reflete o estado do projeto a partir do momento em que ele foi extraído.  
  
 Cliente  
 Um programa que usa o sistema de controle de código fonte. Para fins desta documentação é o IDE do Visual Studio.  
  
 Comentário  
 Uma mensagem que descreve as alterações que um usuário pode se conectar a uma revisão quando uma operação de controle de origem.  
  
 Conflito  
 Uma situação em que dois usuários tentam fazer check-in de alterações para a mesma região do mesmo arquivo. Normalmente, uma mesclagem deve ser executada.  
  
 Diretório  
 Uma pasta local do cliente é chamada de um diretório. Essa é a cópia em que um usuário realmente faz as alterações. Pode haver muitas cópias de trabalho de um determinado projeto; Geralmente, cada desenvolvedor tem sua própria cópia.  
  
 Obter  
 Uma operação get traz cópia de trabalho do usuário atualizada com a cópia do repositório. Ao contrário de um check-out, um get é executado quando o usuário simplesmente precisa a cópia mais recente, mas pretende sem fazer alterações.  
  
 Histórico  
 Geralmente, é um resumo de todos os check-outs, check-ins, atualizações, marcas e versões feitas no repositório de controle de origem.  
  
 IDE  
 Geralmente se refere ao Visual Studio Integrated Development Environment. No entanto, ele pode também se referir a outros ambientes de cliente que reconhece a API de plug-in de controle de origem.  
  
 Mesclar  
 O processo durante a qual fonte de dois ou mais arquivos de código são combinados para formar um novo arquivo que incorpora todos os recursos de arquivos anteriores. Esse conceito é vital no controle de versão em que dois ou mais desenvolvedores trabalham em arquivos simultaneamente.  
  
 Projeto  
 Uma pasta de controle de origem é conhecida como um projeto. Isso não tem nenhuma relação com soluções ou projetos no Visual Studio.  
  
 Plug-in  
 Uma DLL que fornece funcionalidade de controle do código-fonte, Implementando a API de plug-in de controle de origem.  
  
 Repositório  
 A cópia principal sistema de controle de uma fonte de onde armazena o histórico de revisão completa do projeto. Cada projeto tem exatamente um repositório.  
  
 Revisão  
 Uma alteração confirmada no histórico de um arquivo ou conjunto de arquivos. Uma revisão é um instantâneo em um projeto continuamente em alteração.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
