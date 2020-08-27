---
title: try-except, instruction
description: Référence Microsoft C++ aux instructions de gestion des exceptions structurées en __try et __except.
ms.date: 08/25/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
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
ms.openlocfilehash: 226c3a3df39f284d9c1267051114fc39db358f55
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898621"
---
# <a name="try-except-statement"></a>Instruction `try-except`

L' `try-except` instruction est une extension **spécifique à Microsoft** qui prend en charge la gestion structurée des exceptions dans les langages C et C++.

```cpp
    // . . .
    __try {
        // guarded code
    }
    __except ( /* filter expression */ ) {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>Grammaire

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

## <a name="remarks"></a>Notes

L' `try-except` instruction est une extension Microsoft des langages C et C++. Il permet aux applications cibles de prendre le contrôle lorsque des événements se produisent et qui terminent normalement l’exécution du programme. Ces événements sont appelés *exceptions structurées*, ou *exceptions* pour Short. Le mécanisme qui gère ces exceptions est appelé *gestion structurée des exceptions* (SEH).

Pour obtenir des informations connexes, consultez l' [instruction try-finally](../cpp/try-finally-statement.md).

Les exceptions peuvent être basées sur le matériel ou sur les logiciels. La gestion structurée des exceptions est utile même lorsque les applications ne peuvent pas complètement récupérer à partir d’exceptions matérielles ou logicielles. La SEH permet d’afficher des informations sur l’erreur et d’intercepter l’état interne de l’application pour aider à diagnostiquer le problème. C’est particulièrement utile pour les problèmes intermittents qui ne sont pas faciles à reproduire.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n’est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes C++, nous vous recommandons d’utiliser la gestion des exceptions C++ native : instructions [try, catch et Throw](../cpp/try-throw-and-catch-statements-cpp.md) .

L’instruction composée après la **`__try`** clause est le *corps* ou la section *protégée* . L' **`__except`** expression est également appelée expression de *filtre* . Sa valeur détermine la façon dont l’exception est gérée. L’instruction composée après la **`__except`** clause est le gestionnaire d’exceptions. Le gestionnaire spécifie les actions à effectuer si une exception est levée pendant l’exécution de la section de corps. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Si aucune exception ne se produit pendant l’exécution de la section protégée, l’exécution se poursuit à l’instruction qui suit la **`__except`** clause.

1. Si une exception se produit pendant l’exécution de la section protégée ou dans une routine appelée par la section protégée, l' **`__except`** expression est évaluée. Il existe trois valeurs possibles :

   - `EXCEPTION_CONTINUE_EXECUTION` (-1) L’exception est ignorée. Poursuivre l'exécution au point où l'exception s'est produite.

   - `EXCEPTION_CONTINUE_SEARCH` (0) l’exception n’est pas reconnue. Continuez à rechercher un gestionnaire dans la pile, tout d’abord pour contenir des `try-except` instructions, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - `EXCEPTION_EXECUTE_HANDLER` (1) l’exception est reconnue. Transférez le contrôle au gestionnaire d’exceptions en exécutant l' **`__except`** instruction composée, puis poursuivez l’exécution après le **`__except`** bloc.

L' **`__except`** expression est évaluée comme une expression C. Elle est limitée à une valeur unique, à l’opérateur d’expression conditionnelle ou à l’opérateur virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

Chaque application peut avoir son propre gestionnaire d'exceptions.

Il n’est pas possible d’entrer dans une **`__try`** instruction, mais valide d’en sortir un. Le gestionnaire d’exceptions n’est pas appelé si un processus est terminé au milieu de l’exécution d’une `try-except` instruction.

Pour la compatibilité avec les versions précédentes, **_try**, **_except**et **_leave** sont des synonymes de **`__try`** , **`__except`** et, **`__leave`** sauf si l’option de compilateur [/za désactive les extensions de \( langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

### <a name="the-__leave-keyword"></a><a name="__leave"></a>`__leave`Mot clé

Le **`__leave`** mot clé est valide uniquement dans la section protégée d’une `try-except` instruction, et son effet est d’accéder à la fin de la section protégée. L'exécution se poursuit à la première instruction située après le gestionnaire d'exceptions.

Une **`goto`** instruction peut également sortir de la section protégée et elle ne dégrade pas les performances, comme c’est le cas dans une instruction **try-finally** . Cela est dû au fait que le déroulement de la pile ne se produit pas. Toutefois, nous vous recommandons d’utiliser le **`__leave`** mot clé plutôt qu’une **`goto`** instruction. La raison est que vous êtes moins susceptible de faire une erreur de programmation si la section protégée est volumineuse ou complexe.

### <a name="structured-exception-handling-intrinsic-functions"></a>Fonctions intrinsèques de gestion structurée des exceptions

La gestion structurée des exceptions fournit deux fonctions intrinsèques qui peuvent être utilisées avec l' `try-except` instruction : [GetExceptionCode](/windows/win32/Debug/getexceptioncode) et [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode` retourne le code (entier 32 bits) de l’exception.

La fonction intrinsèque `GetExceptionInformation` retourne un pointeur vers une structure [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) contenant des informations supplémentaires sur l’exception. Ce pointeur vous permet d'accéder à l'état de l'ordinateur qui existait au moment d'une exception matérielle. La structure est comme suit :

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Les types de pointeurs `PEXCEPTION_RECORD` et `PCONTEXT` sont définis dans le fichier include \<winnt.h> , et `_EXCEPTION_RECORD` et `_CONTEXT` sont définis dans le fichier include \<excpt.h>

Vous pouvez utiliser `GetExceptionCode` dans le gestionnaire d’exceptions. Toutefois, vous pouvez utiliser `GetExceptionInformation` uniquement dans l’expression de filtre d’exception. Les informations vers lesquelles il pointe se trouvent généralement sur la pile et ne sont plus disponibles lorsque le contrôle est transféré au gestionnaire d’exceptions.

La fonction intrinsèque [AbnormalTermination](/windows/win32/Debug/abnormaltermination) est disponible dans un gestionnaire de terminaisons. Elle retourne 0 si le corps de l’instruction **try-finally** se termine de manière séquentielle. Dans tous les autres cas, elle retourne 1.

\<excpt.h> définit des noms de remplacement pour ces fonctions intrinsèques :

`GetExceptionCode` équivaut à `_exception_code`

`GetExceptionInformation` équivaut à `_exception_info`

`AbnormalTermination` équivaut à `_abnormal_termination`

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

### <a name="output"></a>Output

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

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
