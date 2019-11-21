---
title: Structured Exception Handling (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 942a7e48e4315454476bfe93c68169f461b006b2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245128"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

Structured exception handling (SEH) is a Microsoft extension to C to handle certain exceptional code situations, such as hardware faults, gracefully. Although Windows and Microsoft C++ support SEH, we recommend that you use ISO-standard C++ exception handling because it makes your code more portable and flexible. Nevertheless, to maintain existing code or for particular kinds of programs, you still might have to use SEH.

**Microsoft specific:**

## <a name="grammar"></a>Grammaire

*try-except-statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__except** **(** *expression* **)** *compound-statement*

*try-finally-statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__finally** *compound-statement*

## <a name="remarks"></a>Notes

With SEH, you can ensure that resources such as memory blocks and files are released correctly if execution unexpectedly terminates. You can also handle specific problems—for example, insufficient memory—by using concise structured code that does not rely on **goto** statements or elaborate testing of return codes.

Les instructions try-except et try-finally référencées dans cet article sont des extensions Microsoft du langage C. Elles prennent en charge SEH en permettant aux applications de prendre le contrôle d'un programme après des événements qui termineraient sinon son exécution. Bien que la gestion SEH fonctionne avec des fichiers sources C++, elle n'est pas spécifiquement conçue pour C++. If you use SEH in a C++ program that you compile by using the [/EHa or /EHsc](../build/reference/eh-exception-handling-model.md) option, destructors for local objects are called but other execution behavior might not be what you expect. For an illustration, see the example later in this article. In most cases, instead of SEH we recommend that you use ISO-standard [C++ exception handling](../cpp/try-throw-and-catch-statements-cpp.md), which the Microsoft C++ compiler also supports. En utilisant la gestion des exceptions C++, vous pouvez garantir que votre code est plus portable et gérer les exceptions de tout type.

If you have C code that uses SEH, you can mix it with C++ code that uses C++ exception handling. For information, see [Handle structured exceptions in C++](../cpp/exception-handling-differences.md).

Il existe deux mécanismes de gestion SEH :

- [Exception handlers](../cpp/writing-an-exception-handler.md), or **__except** blocks, which can respond to or dismiss the exception.

- [Termination handlers](../cpp/writing-a-termination-handler.md), or **__finally** blocks, which are always called, whether an exception causes termination or not.

Ces deux types de gestionnaires sont distincts, mais sont étroitement liés via un processus appelé « déroulement de la pile ». When a structured exception occurs, Windows looks for the most recently installed exception handler that is currently active. Le gestionnaire peut effectuer l'une des trois opérations suivantes :

- Il ne reconnaît pas l'exception et passe le contrôle à d'autres gestionnaires.

- Il reconnaît l'exception, mais la fait disparaître.

- Il reconnaît l'exception et la gère.

Le gestionnaire d'exceptions qui reconnaît l'exception peut ne pas être dans la fonction qui s'exécutait quand l'exception s'est produite. Dans certains cas, il peut s'agir d'une fonction beaucoup plus élevée dans la pile. La fonction en cours d'exécution et toutes les autres fonctions sur le frame de pile sont terminées. During this process, the stack is "unwound;" that is, local non-static variables of terminated functions are cleared from the stack.

Tout en déroulant la pile, le système d'exploitation appelle tous les gestionnaires de terminaisons que vous avez écrits pour chaque fonction. En utilisant un gestionnaire de terminaisons, vous pouvez nettoyer les ressources qui autrement resteraient ouvertes en raison d'un achèvement anormal. If you've entered a critical section, you can exit it in the termination handler. Si le programme doit s'arrêter, vous pouvez effectuer d'autres tâches de gestion interne telles que la fermeture et la suppression des fichiers temporaires.

## <a name="next-steps"></a>Étapes suivantes

- [Writing an exception handler](../cpp/writing-an-exception-handler.md)

- [Writing a termination handler](../cpp/writing-a-termination-handler.md)

- [Gérer les exceptions structurées en C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Exemple

As stated earlier, destructors for local objects are called if you use SEH in a C++ program and compile it by using the **/EHa** or **/EHsc** option. Toutefois, le comportement pendant l'exécution peut ne pas être celui prévu si vous utilisez également des exceptions C++. This example demonstrates these behavioral differences.

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

If you use **/EHsc** to compile this code but the local test control macro `CPPEX` is undefined, there is no execution of the `TestClass` destructor and the output looks like this:

```Output
Triggering SEH exception
Executing SEH __except block
```

If you use **/EHsc** to compile the code and `CPPEX` is defined by using `/DCPPEX` (so that a C++ exception is thrown), the `TestClass` destructor executes and the output looks like this:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

If you use **/EHa** to compile the code, the `TestClass` destructor executes regardless of whether the exception was thrown by using `std::throw` or by using SEH to trigger the exception, that is, whether `CPPEX` defined or not. La sortie ressemble à ceci :

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md).

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[Errors and Exception Handling](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Structured Exception Handling (Windows)](/windows/win32/debug/structured-exception-handling)
