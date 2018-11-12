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
ms.openlocfilehash: 0a243225d1569bd203090085e1817bef7094f1e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614719"
---
# <a name="try-except-statement"></a>try-except, instruction

**Section spécifique à Microsoft**

Le **essayez-sauf** instruction est une extension Microsoft C et langages C++ qui prend en charge de gestion des exceptions structurées.

## <a name="syntax"></a>Syntaxe

> **__try** <br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;code protégé<br/>
> }<br/>
> **__except** ( *expression* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;code du Gestionnaire d’exception<br/>
> }<br/>

## <a name="remarks"></a>Notes

Le **essayez-sauf** instruction est une extension Microsoft C et langages C++ qui permet aux applications cibles obtenir des contrôlent lorsque surviennent des événements qui terminent normalement l’exécution du programme. Ces événements sont appelés *exceptions*, et le mécanisme des exceptions est appelé *structurée des exceptions* (SEH).

Pour plus d’informations, consultez le [instruction try-finally](../cpp/try-finally-statement.md).

Les exceptions peuvent être basées sur le matériel ou sur des logiciels. Même quand les applications ne peuvent pas complètement récupérer à partir d'exceptions matérielles ou logicielles, la gestion structurée des exceptions permet d'afficher des informations sur l'erreur et d'intercepter l'état interne de l'application pour favoriser le diagnostic du problème. Ceci s'avère particulièrement utile pour les problèmes intermittents qui ne peuvent pas être facilement reproduits.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes C++, il est recommandé d’utiliser le mécanisme de gestion des exceptions C++ ([try, catch et throw](../cpp/try-throw-and-catch-statements-cpp.md) instructions).

L’instruction composée après la **__try** clause est le corps ou la section protégée. L’instruction composée après la **__except** clause est le Gestionnaire d’exceptions. Le gestionnaire spécifie un ensemble d'actions à entreprendre si une exception est levée pendant l'exécution du corps de la section protégée. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Si aucune exception ne se produit pendant l’exécution de la section protégée, l’exécution se poursuit à l’instruction après le **__except** clause.

1. Si une exception se produit pendant l’exécution de la section protégée ou dans toute routine de la section protégée, la **__except** *expression* (appelée la *filtre* expression) est évaluée et la valeur détermine comment l’exception est gérée. Il existe trois valeurs possibles :

   - Exception de EXCEPTION_CONTINUE_EXECUTION (-1) a été abandonnée. Poursuivre l'exécution au point où l'exception s'est produite.

   - Exception de EXCEPTION_CONTINUE_SEARCH (0) n’est pas reconnue. Poursuivre la recherche d’un gestionnaire dans la pile, en premier pour qu’il contienne des instructions **try-except**, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - Exception_execute_handler (1) l’Exception est reconnue. Transférer le contrôle au gestionnaire d’exceptions en exécutant la **__except** une instruction composée, puis poursuivre l’exécution après le **__except** bloc.

Étant donné que le **__except** expression est évaluée comme une expression C, elle est limitée à une valeur unique, l’opérateur d’expression conditionnelle ou l’opérateur virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

Chaque application peut avoir son propre gestionnaire d'exceptions.

Il n’est pas valide de sauter dans une **__try** mais valide de sauter hors d’une instruction. Le Gestionnaire d’exceptions n’est pas appelé si un processus est terminé au milieu de l’exécution un **essayez-sauf** instruction.

Pour assurer la compatibilité avec les versions précédentes, **_try**, **_except**, et **_leave** sont synonymes de **__try**, **__except** , et **__leave** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

### <a name="the-leave-keyword"></a>Mot clé __leave

Le **__leave** mot clé est valide uniquement dans la section protégée d’un **essayez-sauf** instruction et son effet consiste à accéder à la fin de la section protégée. L'exécution se poursuit à la première instruction située après le gestionnaire d'exceptions.

Un **goto** instruction peut également sortir de la section protégée, et il ne réduit pas les performances comme il le fait un **try-finally** instruction parce que le déroulement de pile ne figure pas. Toutefois, nous vous recommandons d’utiliser le **__leave** mot-clé au lieu d’un **goto** instruction parce que vous êtes moins enclin à commettre une erreur de programmation si la section protégée est volumineux ou complexes.

### <a name="structured-exception-handling-intrinsic-functions"></a>Fonctions intrinsèques de gestion structurée des exceptions

Gestion structurée des exceptions fournit deux fonctions intrinsèques qui sont disponibles à utiliser avec le **essayez-sauf** instruction : `GetExceptionCode` et `GetExceptionInformation`.

`GetExceptionCode` Retourne le code (un entier 32 bits) de l’exception.

La fonction intrinsèque `GetExceptionInformation` retourne un pointeur vers une structure contenant des informations supplémentaires relatives à l’exception. Ce pointeur vous permet d'accéder à l'état de l'ordinateur qui existait au moment d'une exception matérielle. La structure est la suivante :

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Les types pointeur `PEXCEPTION_RECORD` et `PCONTEXT` sont définis dans le fichier include \<winnt.h >, et `_EXCEPTION_RECORD` et `_CONTEXT` sont définis dans le fichier include \<excpt.h >

Vous pouvez utiliser `GetExceptionCode` dans le Gestionnaire d’exceptions. Toutefois, vous pouvez utiliser `GetExceptionInformation` uniquement au sein de l’expression de filtre d’exception. Les informations qu'il désigne sont généralement sur la pile et ne sont plus disponibles lorsque le contrôle est transféré au gestionnaire d'exceptions.

La fonction intrinsèque `AbnormalTermination` est disponible au sein d’un gestionnaire de terminaisons. Elle retourne 0 si le corps de la **try-finally** instruction se termine séquentiellement. Dans tous les autres cas, elle retourne 1.

excpt.h définit d’autres noms pour ces fonctions intrinsèques :

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
