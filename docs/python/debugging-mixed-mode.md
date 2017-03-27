---
title: "Depuração de modo misto nas Ferramentas Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca86a87-e254-4ab7-b3ba-a0ab99c1da93
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 1e1f72619618d252c43537093b9ebd30eee715ab
ms.lasthandoff: 03/10/2017

---

# <a name="debugging-python-and-c-together"></a>Depurando o Python e o C++ juntos

Os depuradores do Python mais comuns, incluindo a PTVS (Ferramentas Python para Visual Studio) antes da versão 2.0, dão suporte apenas à depuração de código do Python. No entanto, na prática, o Python é usado em conjunto com o C ou o C++, nos casos em que é necessário o alto desempenho ou a capacidade de invocar diretamente as APIs da plataforma. A PTVS 2.0 e posterior (em qualquer edição do Visual Studio) fornece a depuração de modo misto integrada e simultânea nativa (C/C++) e para o Python, com pilhas de chamadas combinadas, a capacidade de depurar entre o código do Python e o código nativo, pontos de interrupção em um desses tipos de código e a capacidade de ver representações do Python de objetos em quadros nativos e vice-versa:

![Depuração de modo misto](media/mixed-mode-debugging.png) 

Para obter uma introdução à compilação, ao teste e à depuração de módulos nativos do C com o Visual Studio, assista a [Deep Dive: Creating Native Modules](https://youtu.be/D9RlT06a1EI) (Aprofundamento: Criar módulos nativos) (youtube.com, 9min9s).

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

## <a name="enabling-mixed-mode-debugging"></a>Habilitando a depuração de modo misto

1. Clique com o botão direito do mouse no projeto, no Gerenciador de Soluções, selecione **Propriedades**, selecione a guia **Depuração** e, em seguida, ative a opção para **Habilitar a depuração de código nativo**. Isso habilita o modo misto em todas as sessões de depuração.

    ![Habilitando a depuração de código nativo](media/mixed-mode-debugging-enable-native.png)

1. Ao anexar o depurador de modo misto a um processo existente (**Depurar > Anexar ao Processo...**), selecione o botão **Selecionar...** para abrir a caixa de diálogo **Selecionar Tipo de Código**, defina a opção **Depurar esses tipos de código** e selecione **Nativo** e **Python** na lista:

    ![Selecionando os tipos de código Nativo e do Python](media/mixed-mode-debugging-code-type.png)

    As configurações de tipo de código são persistentes; portanto, se desejar desabilitar a depuração de modo misto ao se anexar a um processo diferente mais tarde, você precisará repetir essas etapas e desmarcar o tipo de código Python.

    É possível selecionar outros tipos de código além do **Nativo** ou em vez dele. Por exemplo, se um aplicativo gerenciado hospedar o CPython, que, por sua vez, usa módulos de extensão nativos e você desejar depurar todos os três, é possível marcar **Python**, **Nativo** e Gerenciado** juntos para uma experiência de depuração unificada, incluindo pilhas de chamadas combinadas e a execução em etapas entre os três tempos de execução.

1. Ao iniciar a depuração no modo misto pela primeira vez, provavelmente, você verá uma caixa de diálogo **Símbolos Obrigatórios do Python**. Consulte [Símbolos para a depuração de modo misto](debugging-symbols-for-mixed-mode.md) para obter detalhes. Você precisa instalar símbolos apenas uma vez para qualquer ambiente do Python.


## <a name="mixed-mode-specific-features"></a>Recursos específicos ao modo misto

- [Pilha de chamadas combinada](#combined-call-stack)
- [Execução em etapas entre o código do Python e o código nativo](#stepping-between-python-and-native-code)
- [Exibição de valores PyObject no código nativo](#pyobject-values-in-native-code)
- [Exibição de valores Nativos no código do Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Pilha de chamadas combinada

A janela Pilha de Chamadas mostra os registros de ativação nativo e do Python intercalados, com transições marcadas entre os dois:

![Pilha de chamadas combinada](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> As transições serão exibidas como “[Código Externo]”, sem especificar a direção da transição, se a opção **Ferramentas > Opções > Depuração > Geral > Habilitar Apenas Meu Código** estiver definida.

Clicar duas vezes em um quadro de chamada o torna ativo e abre o código-fonte apropriado, se possível. Se o código-fonte não estiver disponível, o quadro ainda ficará ativo e as variáveis locais poderão ser inspecionadas.

### <a name="stepping-between-python-and-native-code"></a>Execução em etapas entre o código do Python e o código nativo

Ao usar os comandos Intervir (F11) ou Depuração Circular (Shift+F11), o depurador de modo misto manipulará corretamente as alterações entre os tipos de código. Por exemplo, quando o Python chama um método de um tipo implementado no C, a intervenção em uma chamada a esse método é interrompida no início da função nativa que implementa o método. Da mesma forma, quando o código nativo chama uma função de API do Python, isso resulta na invocação do código do Python. Por exemplo, a intervenção em um `PyObject_CallObject` em um valor de função que foi originalmente definido no Python é interrompida no início da função do Python. Também há suporte para a intervenção do Python para nativo em funções nativas invocadas do Python por meio de [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Exibição de valores PyObject no código nativo

Quando um quadro nativo (C ou C++) está ativo, suas variáveis locais são mostradas na janela Locais do depurador. Nos módulos de extensão nativos do Python, muitos deles são do tipo `PyObject` (que é um typedef de `_object`) ou alguns outros tipos fundamentais do Python (consulte a lista abaixo). Na depuração de modo misto, esses valores apresentam um nó filho adicional rotulado “exibição do Python”. Quando expandido, esse nó mostra a representação do Python da variável, idêntico ao que você veria se uma variável local que referencia o mesmo objeto estivesse presente em um quadro do Python. Os filhos desse nó são editáveis.

![Exibição do Python](media/mixed-mode-debugging-python-view.png)

Para desabilitar esse recurso, clique com o botão direito do mouse em qualquer lugar da janela Locais e ative/desative a opção de menu **Python > Mostrar Nós de Exibição do Python**:

![Habilitando a exibição do Python](media/mixed-mode-debugging-enable-python-view.png)

Tipos C que mostram nós “[Exibição do Python]” (se estiverem habilitados):

- `PyObject `
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

“[Exibição do Python]” não é mostrada automaticamente para tipos criados por conta própria. Ao criar extensões para o Python 3.x, geralmente, isso não é um problema, pois qualquer objeto, em última análise, tem um campo `ob_base` de um dos tipos acima, o que faz com que “[Exibição do Python]” seja mostrado. 

No entanto, para o Python 2.x, cada tipo de objeto normalmente declara seu cabeçalho como uma coleção de campos embutidos e não há nenhuma associação entre os tipos criados personalizados e `PyObject` no nível do sistema de tipos do código C/C++. Para habilitar nós “[Exibição do Python]” para esses tipos personalizados, edite o `PythonDkm.natvis` no [diretório de instalação das ferramentas Python](installation.md#install-locations) e apenas adicione outro elemento ao XML do struct do C ou da classe do C++.

Uma opção alternativa (e melhor) é seguir o [PEP 3123](http://www.python.org/dev/peps/pep-3123/) e usar um campo `PyObject ob_base;` explícito em vez de `PyObject_HEAD`, embora isso nem sempre seja possível por motivos de compatibilidade com versões anteriores.


### <a name="native-values-view-in-python-code"></a>Exibição de valores Nativos no código do Python

Semelhante à seção anterior, é possível habilitar uma “[Exibição do C++]” para valores nativos na janela Locais quando um quadro do Python está ativo. Esse recurso não está habilitado por padrão; portanto, ative-o clicando com o botão direito do mouse na janela Locais e ativando/desativando a opção de menu **Python > Mostrar Nós de Exibição do C++**.

![Habilitando a exibição do C++](media/mixed-mode-debugging-enable-cpp-view.png)

O nó “[Exibição do C++]” fornece uma representação da estrutura subjacente do C/C++ de um valor, idêntico ao que você veria em um quadro nativo. Por exemplo, ele mostra uma instância de `_longobject` (para a qual `PyLongObject` é um typedef) de um inteiro longo no Python e tentará inferir tipos para as classes nativas criadas por conta própria. Os filhos desse nó são editáveis.

![Exibição do C++](media/mixed-mode-debugging-cpp-view.png)

Se um campo filho de um objeto for do tipo `PyObject` ou um dos outros tipos com suporte, ele terá um nó de representação “[Exibição do Python]” (se ele estiver habilitado), possibilitando o acesso a gráficos de objeto em que links não são diretamente expostos ao Python.

Ao contrário de nós “[Exibição do Python]”, que usam metadados de objeto do Python para determinar o tipo do objeto, não há nenhum mecanismo similarmente confiável para a “[Exibição do C++]”. Em termos gerais, considerando um valor do Python (ou seja, uma referência `PyObject`), não é possível determinar com confiança qual estrutura do C/C++ está dando suporte a ele. O depurador de modo misto tenta adivinhar esse tipo observando vários campos do tipo do objeto (como o `PyTypeObject` referenciado por seu campo `ob_type`) que têm tipos de ponteiro de função. Se um desses ponteiros de função referenciar uma função que pode ser resolvida e essa função tiver um parâmetro `self` com um tipo mais específico que `PyObject*`, esse tipo será considerado como o tipo de suporte. Por exemplo, se `ob_type->tp_init` de um objeto especificado apontar para a seguinte função:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

o depurador poderá deduzir corretamente que o tipo C do objeto é `FobObject`. Se não for possível determinar um tipo mais preciso de `tp_init`, ele seguirá para outros campos. Se não for possível deduzir o tipo de nenhum desses campos, o nó “[Exibição do C++]” apresentará o objeto como uma instância `PyObject`.

Para obter sempre uma representação útil de tipos criados personalizados, é melhor registrar, pelo menos, uma função especial ao registrar o tipo e usar um parâmetro `self` fortemente tipado. A maioria dos tipos atende a esse requisito naturalmente; se não for o caso, geralmente, `tp_init` será a entrada mais conveniente a ser usada para essa finalidade. Uma implementação fictícia de `tp_init` de um tipo que está presente exclusivamente para habilitar a inferência de tipos do depurador pode apenas retornar zero imediatamente, como no exemplo de código acima.

## <a name="differences-from-standard-python-debugging"></a>Diferenças da depuração padrão do Python

O depurador de modo misto é diferente do [depurador padrão do Python](debugging.md), que introduz alguns recursos adicionais, mas que não contém algumas funcionalidades relacionadas ao Python:

- Recursos sem suporte: pontos de interrupção condicionais, janela Interativa de Depuração e depuração remota de plataforma cruzada.
- Janela imediata: disponível, mas com um subconjunto limitado de sua funcionalidade, incluindo todas as limitações listadas aqui.
- Versões do Python com suporte: somente CPython 2.7 e 3.3+.
- Shell do Visual Studio: ao usar a PTVS com o Shell do Visual Studio (por exemplo, se ele foi instalado usando o instalador integrado), o Visual Studio não poderá abrir projetos do C++ e a experiência de edição em arquivos do C++ será apenas a de um editor de texto básico. No entanto, há suporte completo para a depuração do C/C++ e a depuração de modo misto no Shell com código-fonte, execução em etapas em código nativo e avaliação de expressão do C++ nas janelas do depurador.
- Exibindo e expandindo objetos: ao exibir objetos do Python nas janelas Locais e Inspeção da ferramenta do depurador, o depurador de modo misto mostra apenas a estrutura dos objetos. Ele não avalia propriedades automaticamente nem mostra atributos computados. Para coleções, ele mostra apenas os elementos de tipos de coleção interna (`tuple`, `list`, `dict`, `set`). Os tipos de coleção personalizada não são visualizados como coleções, a menos que sejam herdados de algum tipo de coleção interna.
- Avaliação de expressão: consulte abaixo.

### <a name="expression-evaluation"></a>Avaliação de expressão

O depurador padrão do Python permite a avaliação de expressões arbitrárias do Python nas janelas Inspeção e Imediata quando o processo depurado está em pausa em qualquer ponto do código, desde que ele não esteja bloqueado em uma operação de E/S ou em outra chamada do sistema semelhante. Na depuração de modo misto, expressões arbitrárias podem ser avaliadas somente quando interrompidas no código do Python, após um ponto de interrupção ou a execução em etapas do código e as expressões podem ser avaliadas somente no thread em que ocorreu o ponto de interrupção ou a operação de execução em etapas.

Quando interrompida no código nativo ou no código do Python quando as condições acima não se aplicarem (por exemplo, após uma operação de depuração circular ou em um thread diferente), a avaliação da expressão é limitada ao acesso das variáveis locais e globais no escopo do quadro atualmente selecionado, ao acesso de seus campos e à indexação de tipos de coleção interna com literais. Por exemplo, a seguinte expressão pode ser avaliada em qualquer contexto (desde que todos os identificadores refiram-se a variáveis e a campos existentes dos tipos apropriados):

```python
foo.bar[0].baz['key']
```

O depurador de modo misto também resolve essas expressões de outra forma. Todas as operações de acesso a membro pesquisam somente os campos que fazem parte diretamente do objeto (como uma entrada em seu `__dict__` ou `__slots__`, ou um campo de um struct nativo que é exposto ao Python por meio de `tp_members`) e ignoram qualquer `__getattr__`, `__getattribute__` ou lógica do descritor. Da mesma forma, todas as operações de indexação ignoram `__getitem__` e acessam as estruturas de dados internas das coleções diretamente.

Para fins de consistência, esse esquema de resolução de nomes é usado para todas as expressões que correspondem às restrições de avaliação de expressão limitada, independentemente se as expressões arbitrárias são permitidas ou não no ponto de interrupção atual. Para forçar a semântica correta do Python quando um avaliador completo está disponível, coloque a expressão entre parênteses:

```python
(foo.bar[0].baz['key'])
```
