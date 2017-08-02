---
title: Teste de Unidade do Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2597583912c7694495617c53839f41aa13cda871
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Configurando o teste de unidade para o código do Python

Testes de unidade são partes do código que testam outras unidades de código em um aplicativo, normalmente, funções isoladas, classes e assim por diante. Quando um aplicativo é aprovado em todos os seus testes de unidade, pelo menos, é possível confiar que sua funcionalidade de baixo nível está correta.

O Python usa testes de unidade extensivamente para validar cenários durante a criação de um programa. O suporte do Python no Visual Studio inclui descoberta, execução e depuração de testes de unidade no contexto do processo de desenvolvimento, em vez de precisar executá-los separadamente.

Este tópico fornece uma breve descrição das funcionalidades de teste de unidade no Visual Studio com o Python. Para obter mais informações sobre testes de unidade em geral, consulte [Executar um teste de unidade no código](../test/unit-test-your-code.md).

## <a name="discovering-and-viewing-tests"></a>Descobrindo e exibindo testes

Por convenção, o Visual Studio identifica os testes como métodos cujos nomes começam com “test”. Para ver isso, faça o seguinte:

1. Abra um [projeto do Python](python-projects.md) carregado no Visual Studio, clique com o botão direito do mouse no projeto, selecione **Adicionar > Novo Item...** e selecione **Teste de Unidade do Python** seguido por **Adicionar**.

1. Isso cria um arquivo test1.py com um código que importa o módulo `unittest` padrão, deriva uma classe de teste de `unittest.TestCase` e invoca `unittest.main()` se o script é executado diretamente:

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. Salve o arquivo se necessário e, em seguida, abra o Gerenciador de Testes com o comando de menu **Teste > Windows > Gerenciador de Testes**.

1. O Gerenciador de Testes pesquisará testes no projeto e os exibirá, conforme mostrado abaixo. Se você clicar duas vezes em um teste, seu arquivo de origem será aberto.

    ![Gerenciador de Testes mostrando o test_A padrão](~/docs/python/media/unit-test-A.png)

1. Conforme você adiciona mais testes ao projeto, é possível organizar a exibição no Gerenciador de Testes usando o menu Agrupar Por na barra de ferramentas:

    ![Menu da barra de ferramentas Agrupar Por do Gerenciador de Testes](~/docs/python/media/unit-test-group-menu.png)

1. Também é possível inserir um texto no campo de pesquisa para filtrar os testes por nome.

Para obter mais detalhes sobre o módulo `unittest` e sobre como escrever testes, consulte a [documentação do Python 2.7](https://docs.python.org/2/library/unittest.html) ou a [documentação do Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Executando testes

No Gerenciador de Testes, é possível executar testes de várias maneiras:

- **Executar Todos** claramente executa todos os testes mostrados (sujeito a filtros).
- O menu **Executar...** fornece comandos para executar testes com falha, aprovados ou não executados como um grupo.
- É possível selecionar um ou mais testes, clicar com o botão direito do mouse e selecionar **Executar Testes Selecionados**.

Os testes são executados em segundo plano e o Gerenciador de Testes atualiza o status de cada teste conforme ele é concluído:

- Os testes aprovados mostram um tique verde e o tempo necessário para executar o teste:

    ![Status do test_A aprovado](~/docs/python/media/unit-test-A-pass.png)

- Os testes com falha mostram uma cruz vermelha com um link **Saída** que mostra a saída do console e a saída `unittest` da execução de teste:

    ![Status do test_A com falha](~/docs/python/media/unit-test-A-fail.png)

    ![test_A com falha com motivo](~/docs/python/media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Depurando testes

Como os testes de unidade são partes do código, eles estão sujeitos a bugs, assim como qualquer outro código e, ocasionalmente, precisam ser executados em um depurador, no qual é possível definir pontos de interrupção, examinar variáveis e executar o código em etapas. O Visual Studio também fornece ferramentas de diagnóstico

Para iniciar a depuração, defina um ponto de interrupção inicial no código, clique com o botão direito do mouse no teste (ou em uma seleção) no Gerenciador de Testes e selecione **Depurar Testes Selecionados**. O Visual Studio iniciará o depurador do Python como faria com o código do aplicativo.

![Depurando um teste](~/docs/python/media/unit-test-debugging.png)

Também é possível usar os comandos **Analisar Cobertura de Código nos Testes Selecionados** e **Teste de Perfil**, dependendo da versão do Visual Studio (consulte a [Matriz de recursos](python-in-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Problemas conhecidos

- Ao iniciar a depuração, o Visual Studio parecerá como se estivesse iniciando e interrompendo a depuração e, em seguida, a iniciará novamente. Isso é esperado.
- Quando estiver depurando vários testes, cada um deles será executado de forma independente, o que interromperá a sessão de depuração.
- O Visual Studio falhará intermitentemente ao iniciar um teste durante a depuração. Normalmente, a tentativa de depurar o teste novamente terá êxito.
- Durante a depuração, é possível executar a depuração circular de um teste na implementação `unittest`. Normalmente, a próxima etapa será executada ao final do programa e interromperá a depuração.
