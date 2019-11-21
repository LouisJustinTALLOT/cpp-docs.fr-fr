---
title: try-except, instruction
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: af378f510f11e1fe7d08619b5f33efe92a13d7be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245160"
---
# <a name="try-except-statement"></a>try-except, instruction

**Section spécifique de Microsoft**

The **try-except** statement is a Microsoft extension to the C and C++ languages that supports structured exception handling.

## <a name="syntax"></a>Syntaxe

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// guarded code<br/>
> }<br/>
> **\_\_except** ( *expression* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// exception handler code<br/>
> }

## <a name="remarks"></a>Notes

The **try-except** statement is a Microsoft extension to the C and C++ languages that enables target applications to gain control when events that normally terminate program execution occur. Such events are called *exceptions*, and the mechanism that deals with exceptions is called *structured exception handling* (SEH).

For related information, see the [try-finally statement](../cpp/try-finally-statement.md).

Les exceptions peuvent être basées sur le matériel ou sur des logiciels. Même quand les applications ne peuvent pas complètement récupérer à partir d'exceptions matérielles ou logicielles, la gestion structurée des exceptions permet d'afficher des informations sur l'erreur et d'intercepter l'état interne de l'application pour favoriser le diagnostic du problème. Ceci s'avère particulièrement utile pour les problèmes intermittents qui ne peuvent pas être facilement reproduits.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. For C++ programs, it is recommended that you use the C++ exception-handling mechanism ([try, catch, and throw](../cpp/try-throw-and-catch-statements-cpp.md) statements).

The compound statement after the **__try** clause is the body or guarded section. The compound statement after the **__except** clause is the exception handler. Le gestionnaire spécifie un ensemble d'actions à entreprendre si une exception est levée pendant l'exécution du corps de la section protégée. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. If no exception occurs during execution of the guarded section, execution continues at the statement after the **__except** clause.

1. If an exception occurs during execution of the guarded section or in any routine the guarded section calls, the **__except** *expression* (called the *filter* expression) is evaluated and the value determines how the exception is handled. Il existe trois valeurs possibles :

   - EXCEPTION_CONTINUE_EXECUTION (-1) Exception is dismissed. Poursuivre l'exécution au point où l'exception s'est produite.

   - EXCEPTION_CONTINUE_SEARCH (0) Exception is not recognized. Poursuivre la recherche d’un gestionnaire dans la pile, en premier pour qu’il contienne des instructions **try-except**, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - EXCEPTION_EXECUTE_HANDLER (1) Exception is recognized. Transfer control to the exception handler by executing the **__except** compound statement, then continue execution after the **__except** block.

Because the **__except** expression is evaluated as a C expression, it is limited to a single value, the conditional-expression operator, or the comma operator. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

Chaque application peut avoir son propre gestionnaire d'exceptions.

It is not valid to jump into a **__try** statement, but valid to jump out of one. The exception handler is not called if a process is terminated in the middle of executing a **try-except** statement.

For compatibility with previous versions, **_try**, **_except**, and **_leave** are synonyms for **__try**, **__except**, and **__leave** unless compiler option [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) is specified.

### <a name="the-__leave-keyword"></a>Mot clé __leave

The **__leave** keyword is valid only within the guarded section of a **try-except** statement, and its effect is to jump to the end of the guarded section. L'exécution se poursuit à la première instruction située après le gestionnaire d'exceptions.

A **goto** statement can also jump out of the guarded section, and it does not degrade performance as it does in a **try-finally** statement because stack unwinding does not occur. However, we recommend that you use the **__leave** keyword rather than a **goto** statement because you are less likely to make a programming mistake if the guarded section is large or complex.

### <a name="structured-exception-handling-intrinsic-functions"></a>Fonctions intrinsèques de gestion structurée des exceptions

Structured exception handling provides two intrinsic functions that are available to use with the **try-except** statement: `GetExceptionCode` and `GetExceptionInformation`.

`GetExceptionCode` returns the code (a 32-bit integer) of the exception.

The intrinsic function `GetExceptionInformation` returns a pointer to a structure containing additional information about the exception. Ce pointeur vous permet d'accéder à l'état de l'ordinateur qui existait au moment d'une exception matérielle. La structure est la suivante :

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

The pointer types `PEXCEPTION_RECORD` and `PCONTEXT` are defined in the include file \<winnt.h>, and `_EXCEPTION_RECORD` and `_CONTEXT` are defined in the include file \<excpt.h>

You can use `GetExceptionCode` within the exception handler. However, you can use `GetExceptionInformation` only within the exception filter expression. Les informations qu'il désigne sont généralement sur la pile et ne sont plus disponibles lorsque le contrôle est transféré au gestionnaire d'exceptions.

The intrinsic function `AbnormalTermination` is available within a termination handler. It returns 0 if the body of the **try-finally** statement terminates sequentially. Dans tous les autres cas, elle retourne 1.

excpt.h defines some alternate names for these intrinsics:

`GetExceptionCode` is equivalent to `_exception_code`

`GetExceptionInformation` is equivalent to `_exception_info`

`AbnormalTermination` is equivalent to `_abnormal_termination`

## <a name="example"></a>Exemple

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Sortie

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
