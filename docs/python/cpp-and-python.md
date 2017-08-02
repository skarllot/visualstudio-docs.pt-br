---
title: Trabalhando com o C++ e o Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "Os processo e as etapas para escrever uma extensão ou um módulo do C++ para o Python no Visual Studio"
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
ms.openlocfilehash: f8a0bef07667e5f876473c966ed3d14a1b84dd0b
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="creating-a-c-extension-for-python"></a>Criando uma extensão do C++ para o Python

Os módulos escritos em C++ (ou em C) são geralmente usados para estender as funcionalidades de um interpretador do Python, bem como para permitir o acesso a funcionalidades de baixo nível do sistema operacional. Há três tipos de módulos principais:

- Módulos de acelerador: como o Python é uma linguagem interpretada, algumas partes do código podem ser escritas em C++ para um desempenho mais alto. 
- Módulos de wrapper: exponha as interfaces existentes do C/C++ ao código do Python ou exponha uma API mais semelhante ao Python que faz uso de recursos de linguagem do Python para facilitar o uso da API.
- Módulos de acesso de baixo nível do sistema: criados para acessar os recursos de baixo nível do tempo de execução CPython, do sistema operacional ou do hardware subjacente. 

Este tópico explica como criar um módulo de extensão do C++ para o CPython que calcula uma tangente hiperbólica e faz uma chamada a ela de um código do Python. Para demonstrar a diferença de desempenho, você criará e testará a rotina primeiro no Python.

A abordagem usada aqui é a mesma usada nas extensões padrão do CPython, conforme descrito na [documentação do Python](https://docs.python.org/3/c-api/). Uma comparação entre esse e outros meios é descrita em [abordagens alternativas](#alternative-approaches) ao final deste tópico.

## <a name="prerequisites"></a>Pré-requisitos

Este passo a passo foi escrito para o Visual Studio 2017 com as cargas de trabalho **Desenvolvimento da Área de Trabalho com o C++** e **Desenvolvimento do Python** com suas opções padrão (como o Python 3.6 como o interpretador padrão). Na carga de trabalho **Desenvolvimento do Python**, marque também a caixa à direita **Ferramentas de desenvolvimento nativo do Python**, que definirá a maior parte das opções descritas neste tópico. (Essa opção também incluirá a carga de trabalho do C++ automaticamente.) 

![Selecionando a opção de ferramentas de desenvolvimento nativo do Python](~/docs/python/media/cpp-install-native.png)

Para obter mais detalhes, consulte [Instalando o suporte do Python para Visual Studio](installation.md), incluindo o uso de outras versões do Visual Studio. Se você instalar o Python separadamente, lembre-se de selecionar **Baixar símbolos de depuração** e **Baixar binários de depuração** em **Opções Avançadas** no instalador. Isso garante que você terá as bibliotecas de depuração necessárias disponíveis se optar por fazer um build de depuração.

> [!Note]
> O Python também está disponível por meio da carga de trabalho **Ciência de dados e aplicativos analíticos**, que inclui o Anaconda 3 de 64 bits (com a versão mais recente do CPython) e a opção **Ferramentas nativas de desenvolvimento do Python** por padrão.

## <a name="create-the-python-application"></a>Criar o aplicativo do Python

1. Crie um novo projeto do Python no Visual Studio selecionando o comando de menu **Arquivo > Novo > Projeto**, pesquisando “Python”, selecionando o modelo **Aplicativo do Python**, fornecendo a ele um nome adequado e uma localização e, em seguida, selecionando **OK**.

1. No arquivo `.py` do projeto, cole o código a seguir que submeterá a benchmark o cálculo de uma tangente hiperbólica (implementada sem o uso da biblioteca de matemática para facilitar a comparação). Fique à vontade para inserir o código manualmente para experimentar alguns [recursos de edição do Python](code-editing.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tanger function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()

        result = fn(DATA)

        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Execute o programa usando **Depurar > Iniciar sem Depuração** (Ctrl + F5) para ver os resultados. Você verá que é necessário alguns segundos para que cada parâmetro de comparação seja concluído.

## <a name="create-the-core-c-project"></a>Criar o projeto principal do C++

1. Clique com o botão direito do mouse na solução, no Gerenciador de Soluções e selecione **Adicionar > Novo Projeto...**. Uma solução do Visual Studio pode conter projetos do Python e do C++ juntos.

1. Pesquise “C++”, selecione **Projeto vazio**, especifique um nome (como TanhBenchmark) e selecione **OK**. Observação: se você tiver instalado as **ferramentas de desenvolvimento nativo do Python** com o Visual Studio 2017, poderá começar com o modelo **Módulo de Extensão do Python**, que implementa grande parte do que já foi descrito aqui. No entanto, para este passo a passo, começar com um projeto vazio demonstrará o build do módulo de extensão passo a passo.

1. Crie um arquivo do C++ no novo projeto clicando com o botão direito do mouse no nó **Arquivos de Origem**, selecione **Adicionar > Novo Item…**, selecione **Arquivo do C++**, fornece a ele um nome (como `module.cpp`) e selecione **OK**. Essa etapa é necessária para ativar as páginas de propriedades do C++ nas próximas etapas.

1. Clique com o botão direito do mouse no novo projeto e selecione **Propriedades**. Em seguida, na parte superior da caixa de diálogo **Páginas de Propriedades** exibida, defina **Configuração** como **Todas as Configurações**.

1. Defina as propriedades específicas, conforme descrito abaixo e selecione **Aplicar** (talvez seja necessário clicar fora de um campo editável para habilitar o botão **Aplicar**).

    | Tabulação | Propriedade | Valor | 
    | --- | --- | --- |
    | Geral | Geral > Nome de Destino | Defina essa opção para que ela corresponda exatamente ao nome do módulo da forma como ele será visto pelo Python. |
    | | Geral > Extensão de Destino | .pyd |
    | | Padrões do Projeto > Tipo de Configuração | Biblioteca Dinâmica (.dll) |
    | C/C++ > Geral | Diretórios de Inclusão Adicionais | Adicione a pasta `include` do Python conforme apropriado para sua instalação, por exemplo, `c:\Python36\include` |     
    | C/C++ > Geração de Código | Biblioteca em Tempo de Execução | DLL com multi-thread (/MD) (consulte Aviso abaixo) |
    | C/C++ > Pré-processador | Definições do Pré-processador | Adicione `Py_LIMITED_API;` ao início da cadeia de caracteres. Isso restringe algumas funções que podem ser chamadas do Python e torna o código mais portátil entre diferentes versões do Python. |
    | Vinculador > Geral | Diretórios de Biblioteca Adicionais | Adicione a pasta `lib` do Python que contém arquivos `.lib` conforme apropriado para sua instalação, por exemplo, `c:\Python36\libs`. (Lembre-se de apontar para a pasta `libs` que contém arquivos `.lib` e *não* para a pasta `Lib` que contém arquivos `.py`.) | 

    > [!Tip]
    > Se a guia C/C++ não for exibida, isso indicará que o projeto não contém nenhum arquivo que ele identifica como arquivos de origem do C/C++. Isso poderá ocorrer se você criar um arquivo de origem sem uma extensão `.c` ou `.cpp`. Por exemplo, se você inseriu `module.coo` em vez de `module.cpp` acidentalmente na nova caixa de diálogo de item anteriormente, o Visual Studio criará o arquivo, mas não definirá o tipo de arquivo como “Código C/C+”, que é o que ativa a guia de propriedades do C/C++. Isso continuará acontecendo mesmo se você renomear o arquivo com `.cpp`. Para corrigir isso, clique com o botão direito do mouse no arquivo no Gerenciador de Soluções, selecione **Propriedades** e, em seguida, defina **Tipo de Arquivo** como **Código C/C++**.

    > [!Warning]
    > Não defina a opção **C/C++ > Geração de Código > Biblioteca em Tempo de Execução** como “DLL de Depuração com Multi-thread (/MDd)” mesmo para uma configuração de Depuração. Você precisa selecionar o tempo de execução “DLL com multi-thread (/MD)” porque é com ele que os binários do Python que não são de depuração são compilados. Se você definir a opção /MDd acidentalmente, você verá o erro *C1189: Py_LIMITED_API é incompatível com Py_DEBUG, Py_TRACE_REFS e Py_REF_DEBUG* ao criar uma configuração de Depuração da DLL. Além disso, se você remover `Py_LIMITED_API` para evitar o erro de build, o Python falhará ao tentar importar o módulo. (A falha ocorrerá na chamada da DLL a `PyModule_Create`, conforme descrito adiante, com a mensagem de saída *Erro fatal do Python: PyThreadState_Get: nenhum thread atual*.)
    >
    > Observe que a opção /MDd é o que é usado para criar os binários de depuração do Python (como python_d.exe), mas sua seleção para uma DLL de extensão ainda causará o erro de build com `Py_LIMITED_API`.
   
1. Clique com o botão direito do mouse no projeto do C++ e selecione **Compilar** para testar as configurações (Depuração e Versão). Observe que você encontrará os arquivos `.pyd` na pasta *Solução* em **Depurar** e **Versão**, não na própria pasta do projeto do C++.

1. Adicione o seguinte código ao arquivo `.cpp` principal do projeto do C++:

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. Compile o projeto do C++ novamente para confirmar se o código está correto.


## <a name="convert-the-c-project-to-an-extension-for-python"></a>Converter o projeto do C++ em uma extensão para o Python

Para transformar a DLL do C++ em uma extensão para o Python, você precisa modificar o método exportado para interagir com tipos do Python. Em seguida, você precisa adicionar uma função que exporta o módulo, juntamente com as definições dos métodos do módulo. Para obter informações sobre o que é mostrado aqui, consulte o [Manual de Referência de API do Python/C](https://docs.python.org/3/c-api/index.html) e, especialmente, [Objetos de módulo](https://docs.python.org/3/c-api/module.html) em python.org. (Lembre-se de selecionar sua versão do Python no controle suspenso no canto superior direito.)

1. No arquivo do C++, inclua `Python.h` na parte superior:

    ```cpp
    include <Python.h>
    ```

1. Modifique o método `tanh` para aceitar e retornar tipos do Python:

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Adicione uma estrutura que define como a função `tanh` do C++ é apresentada ao Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Adicione uma estrutura que define o módulo da forma como ele será visto pelo Python:

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Adicione um método que é chamado pelo Python quando ele carrega o módulo, que deve ser nomeado `PyInit_<module-name>`, em que *&lt;module_name&gt;* corresponde exatamente à propriedade **Geral > Nome de Destino** do Projeto do C++ (ou seja, ele corresponde ao nome de arquivo do `.pyd` criado pelo projeto).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Compile a DLL novamente para verificar o código.

## <a name="test-the-code-and-compare-the-results"></a>Testar o código e comparar os resultados

Agora que você tem a DLL estruturada como uma extensão do Python, é possível consultá-la por meio do projeto do Python, importar o módulo e usar seus métodos.

Há duas maneiras de disponibilizar a DLL para o Python. Primeiro, é possível adicionar uma referência do projeto do Python ao projeto do C++, desde que eles estejam na mesma solução do Visual Studio:

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto do Python e selecione **Referências**. Na caixa de diálogo, selecione a guia **Projetos**, selecione o projeto **superfastcode** e, em seguida, **OK**.

Em segundo lugar, é possível instalar o módulo no ambiente global do Python, disponibilizando-o para outros projetos do Python também. Observe que essa ação normalmente exige que o banco de dados de preenchimento do IntelliSense seja atualizado para esse ambiente, pois ela removerá o módulo do ambiente.

1. Se estiver usando o Visual Studio 2017, execute o instalador do Visual Studio, selecione **Modificar** e selecione **Componentes Individuais > Compiladores, ferramentas de build e tempos de execução > conjunto de ferramentas do Visual C++ 2015.3 v140**. Isso ocorre porque o Python (para o Windows) é o próprio build com o Visual Studio 2015 (versão 14.0) e espera que essas ferramentas estejam disponíveis durante o build de uma extensão por meio do método descrito aqui.

1. Crie um arquivo chamado `setup.py` no projeto do C++ clicando com o botão direito do mouse no projeto, selecionando *Adicionar > Novos Itens...*, pesquisando “Python”, selecionando **arquivo do Python**, nomeando-o setup.py e selecionando **OK**. Quando o arquivo for exibido no editor, cole o seguinte código nele:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    Consulte [Criando extensões do C e C++](https://docs.python.org/3/extending/building.html) (python.org) para obter a documentação sobre esse script.

1. O código `setup.py` instrui o Python a compilar a extensão (usando o conjunto de ferramentas do Visual Studio 2015 C++), o que ocorre na linha de comando. Abra um prompt de comandos com privilégios elevados, navegue para a pasta que contém o projeto do C++ (e `setup.py`) e insira o seguinte comando:

    ```bash
    pip install .
    ```

Agora você pode chamar o código `tanh` e o módulo e comparar seu desempenho com a implementação do Python:

1. Adicione as linhas a seguir a `tanhbenchmark.py` para chamar o método `fast_tanh` exportado da DLL e adicione-o à saída do parâmetro de comparação. Se você digitar a instrução `from s` manualmente, verá `superfastcode` aparecer na lista de conclusão e, depois de digitar `import`, verá o método `fast_tanh`.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Execute o programa do Python e você verá que a rotina do C++ é executada cerca de 15 a 20 vezes mais rápido do que a implementação do Python.

## <a name="debug-the-c-code"></a>Depurar o código C++

O [suporte do Python no Visual Studio](installation.md) inclui a capacidade de [depurar o código do Python e C++ juntos](debugging-mixed-mode.md). Para experimentar isso, faça o seguinte:

1. Clique com o botão direito do mouse no projeto do Python, no Gerenciador de Soluções, selecione **Propriedades**, a guia **Depuração** e, em seguida, a opção **Depurar > Habilitar depuração de código nativo**.

    > [!Tip]
    > Ao habilitar a depuração de código nativo, a janela de saída do Python poderá desaparecer imediatamente quando o programa tiver concluído sem fornecer a pausa comum “Pressione qualquer tecla para continuar...”. Para forçar uma pausa, adicione a opção `-i` ao campo **Executar > Argumentos do Interpretador** na guia **Depurar** ao habilitar a depuração de código nativo. Isso colocará o interpretador do Python no modo interativo após a conclusão do código e, nesse ponto, ele aguardará até que você pressione Ctrl + Z, Enter para sair. (Como alternativa, se você não se importar em modificar o código do Python, poderá adicionar as instruções `import os` e `os.system("pause")` ao final do programa. Isso duplicará o prompt de pausa original.)

1. No código do C++, defina um ponto de interrupção na primeira linha dentro do método `tanh` e, em seguida, inicie o depurador. Você verá o depurador parar quando esse código for chamado:

    ![Parando em um ponto de interrupção no código C++](~/docs/python/media/cpp-debugging.png)

1. Neste ponto, você poderá executar o código C++ em etapas, examinar variáveis e assim por diante, conforme detalhado em [Depurando o C++ e o Python juntos](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Abordagens alternativas 

Há outros meios para criar extensões do Python, conforme descrito na tabela abaixo. A primeira entrada para o CPython é o que já foi discutido neste tópico.

| Abordagem | Ano | Usuários representantes | Vantagens | Desvantagens |
| --- | --- | --- | --- | --- |
| Módulos de extensão do C/C++ para o CPython | 1991 | Biblioteca Padrão | [Tutoriais e documentação abrangente](https://docs.python.org/3/c-api/). Controle total. | Compilação, portabilidade, gerenciamento de referências. Profundo conhecimento sobre o C. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Gere associações para várias linguagens de uma só vez. | Sobrecarga excessiva se o Python for o único destino. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Sem compilação, ampla disponibilidade. | O acesso e a mutação de estruturas do C são complicados e sujeitos a erros. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Semelhante ao Python. Altamente maduro. Alto desempenho. | Compilação, nova sintaxe e cadeia de ferramentas. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Facilidade de integração, compatibilidade com o PyPy. | Novo, menos maduro. |

