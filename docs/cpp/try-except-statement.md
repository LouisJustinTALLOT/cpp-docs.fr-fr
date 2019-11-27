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

**Section spécifique à Microsoft**

L’instruction **try-except** est une extension Microsoft du langage C et C++ des langages qui prennent en charge la gestion structurée des exceptions.

## <a name="syntax"></a>Syntaxe

> **\_\_essayer**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//code protégé<br/>
> }<br/>
> **\_\_except** ( *expression* )<br/>
> {<br/>
> Code du gestionnaire d’exceptions &nbsp;&nbsp;&nbsp;&nbsp;<br/>
> }

## <a name="remarks"></a>Notes

L’instruction **try-except** est une extension Microsoft des langages C C++ et qui permet aux applications cibles de prendre le contrôle lorsque des événements qui terminent normalement l’exécution du programme se produisent. Ces événements sont appelés *exceptions*et le mécanisme qui traite les exceptions est appelé *gestion structurée des exceptions* (SEH).

Pour obtenir des informations connexes, consultez l' [instruction try-finally](../cpp/try-finally-statement.md).

Les exceptions peuvent être basées sur le matériel ou sur des logiciels. Même quand les applications ne peuvent pas complètement récupérer à partir d'exceptions matérielles ou logicielles, la gestion structurée des exceptions permet d'afficher des informations sur l'erreur et d'intercepter l'état interne de l'application pour favoriser le diagnostic du problème. Ceci s'avère particulièrement utile pour les problèmes intermittents qui ne peuvent pas être facilement reproduits.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour C++ les programmes, il est recommandé d’utiliser le C++ mécanisme de gestion des exceptions (instructions[try, catch et Throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

L’instruction composée après la clause **__try** est le corps ou la section protégée. L’instruction composée après la clause **__except** est le gestionnaire d’exceptions. Le gestionnaire spécifie un ensemble d'actions à entreprendre si une exception est levée pendant l'exécution du corps de la section protégée. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Si aucune exception ne se produit pendant l’exécution de la section protégée, l’exécution se poursuit à l’instruction qui suit la clause **__except** .

1. Si une exception se produit pendant l’exécution de la section protégée ou dans toute routine appelée par la section protégée, l' *expression* **__except** (appelée expression de *filtre* ) est évaluée et la valeur détermine la manière dont l’exception est gérée. Il existe trois valeurs possibles :

   - L’exception EXCEPTION_CONTINUE_EXECUTION (-1) est ignorée. Poursuivre l'exécution au point où l'exception s'est produite.

   - L’exception EXCEPTION_CONTINUE_SEARCH (0) n’est pas reconnue. Poursuivre la recherche d’un gestionnaire dans la pile, en premier pour qu’il contienne des instructions **try-except**, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - L’exception EXCEPTION_EXECUTE_HANDLER (1) est reconnue. Transférez le contrôle au gestionnaire d’exceptions en exécutant l’instruction **__except** composée, puis continuez l’exécution après le bloc **__except** .

Étant donné que l’expression **__except** est évaluée comme une expression C, elle est limitée à une valeur unique, à l’opérateur d’expression conditionnelle ou à l’opérateur virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

Chaque application peut avoir son propre gestionnaire d'exceptions.

Il n’est pas possible d’entrer dans une instruction **__try** , mais valide d’en sortir un. Le gestionnaire d’exceptions n’est pas appelé si un processus est terminé au milieu de l’exécution d’une instruction **try-except** .

Pour la compatibilité avec les versions précédentes, **_try**, **_except**et **_leave** sont des synonymes pour **__try**, **__except**et **__leave** , sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

### <a name="the-__leave-keyword"></a>Mot clé __leave

Le mot clé **__leave** est valide uniquement dans la section protégée d’une instruction **try-except** , et son effet est de passer à la fin de la section protégée. L'exécution se poursuit à la première instruction située après le gestionnaire d'exceptions.

Une instruction **goto** peut également sortir de la section protégée, et elle ne dégrade pas les performances, comme c’est le cas dans une instruction **try-finally** , car le déroulement de la pile ne se produit pas. Toutefois, nous vous recommandons d’utiliser le mot clé **__leave** plutôt qu’une instruction **goto** , car vous êtes moins susceptible de faire une erreur de programmation si la section protégée est volumineuse ou complexe.

### <a name="structured-exception-handling-intrinsic-functions"></a>Fonctions intrinsèques de gestion structurée des exceptions

La gestion structurée des exceptions fournit deux fonctions intrinsèques qui peuvent être utilisées avec l’instruction **try-except** : `GetExceptionCode` et `GetExceptionInformation`.

`GetExceptionCode` retourne le code (entier 32 bits) de l’exception.

La fonction intrinsèque `GetExceptionInformation` retourne un pointeur vers une structure contenant des informations supplémentaires sur l’exception. Ce pointeur vous permet d'accéder à l'état de l'ordinateur qui existait au moment d'une exception matérielle. La structure est la suivante :

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Les types de pointeurs `PEXCEPTION_RECORD` et `PCONTEXT` sont définis dans le fichier include \<Winnt. h >, et `_EXCEPTION_RECORD` et `_CONTEXT` sont définis dans le fichier include \<excpt. h >

Vous pouvez utiliser `GetExceptionCode` dans le gestionnaire d’exceptions. Toutefois, vous pouvez utiliser `GetExceptionInformation` uniquement dans l’expression de filtre d’exception. Les informations qu'il désigne sont généralement sur la pile et ne sont plus disponibles lorsque le contrôle est transféré au gestionnaire d'exceptions.

La fonction intrinsèque `AbnormalTermination` est disponible dans un gestionnaire de terminaisons. Elle retourne 0 si le corps de l’instruction **try-finally** se termine de manière séquentielle. Dans tous les autres cas, elle retourne 1.

excpt. h définit d’autres noms pour ces fonctions intrinsèques :

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

**Fin de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
