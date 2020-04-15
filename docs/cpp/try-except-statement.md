---
title: try-except, instruction
description: La référence Microsoft CMD aux __try et __except des instructions de traitement d’exception structurées.
ms.date: 04/03/2020
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
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366235"
---
# <a name="try-except-statement"></a>try-except, instruction

**L’énoncé d’essai-exception** est une extension microsoft qui prend en charge la gestion structurée d’exception dans les langues C et C. Cette extension est **spécifique à Microsoft**.

## <a name="syntax"></a>Syntaxe

> **\_\_Essayer**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;code gardé<br/>
> }<br/>
> sauf ( *expression* ) ** \_ \_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;code de gestionnaire d’exception<br/>
> }

## <a name="remarks"></a>Notes

La déclaration **d’essai-exception** est une extension de Microsoft aux langues C et C. Il permet aux applications cibles de prendre le contrôle lorsque des événements se produisent qui mettent normalement fin à l’exécution du programme. De tels événements sont appelés *exceptions structurées,* ou *exceptions* pour faire court. Le mécanisme qui traite de ces exceptions est appelé *traitement structuré des exceptions* (SEH).

Pour obtenir des informations connexes, voir la [déclaration try-finally](../cpp/try-finally-statement.md).

Les exceptions peuvent être basées sur le matériel ou sur des logiciels. La manipulation structurée des exceptions est utile même lorsque les applications ne peuvent pas complètement récupérer des exceptions matérielles ou logicielles. SEH permet d’afficher des informations d’erreur et de piéger l’état interne de l’application pour aider à diagnostiquer le problème. Il est particulièrement utile pour les problèmes intermittents qui ne sont pas faciles à reproduire.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Cependant, il n’est pas spécialement conçu pour le C. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes CMD, nous vous recommandons d’utiliser la manipulation des exceptions nativeS de CMD : [essayez, attrapez et jetez](../cpp/try-throw-and-catch-statements-cpp.md) des relevés.

L’énoncé composé après la clause **__try** est le *corps* ou la section *gardée.* **L’expression __except** est également connue sous le nom d’expression *de filtre.* Sa valeur détermine la façon dont l’exception est traitée. L’énoncé composé après la clause **de __except** est le gestionnaire d’exception. Le gestionnaire spécifie les mesures à prendre si une exception est soulevée lors de l’exécution de la section du corps. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Si aucune exception n’a lieu lors de l’exécution de la section gardée, l’exécution se poursuit à la déclaration après la **clause __except.**

1. Si une exception se produit lors de l’exécution de la section gardée, ou dans toute routine de la section gardée appelle, **l’expression __except** est évaluée. Il existe trois valeurs possibles :

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) L’exception est rejetée. Poursuivre l'exécution au point où l'exception s'est produite.

   - `EXCEPTION_CONTINUE_SEARCH`(0) L’exception n’est pas reconnue. Poursuivre la recherche d’un gestionnaire dans la pile, en premier pour qu’il contienne des instructions **try-except**, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - `EXCEPTION_EXECUTE_HANDLER`(1) L’exception est reconnue. Transférer le contrôle au gestionnaire d’exception en exécutant la **déclaration du composé __except,** puis continuer l’exécution après le **bloc __except.**

**L’expression __except** est évaluée comme expression C. Il est limité à une seule valeur, l’opérateur d’expression conditionnelle, ou l’opérateur de virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

Chaque application peut avoir son propre gestionnaire d'exceptions.

Il n’est pas valable de sauter dans une **déclaration __try,** mais valide pour sauter hors d’un. Le gestionnaire d’exception n’est pas appelé si un processus est terminé au milieu de l’exécution **d’une déclaration d’essai-sauf.**

Pour la compatibilité avec les versions précédentes, **_try**, **_except**, et **_leave** sont synonymes pour **__try**, **__except**, et **__leave** à moins que l’option compilateur [/Za \(Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

### <a name="the-__leave-keyword"></a>Mot clé __leave

Le mot clé **__leave** n’est valable que dans la section gardée d’une déclaration **d’essai,** et son effet est de sauter à la fin de la section gardée. L'exécution se poursuit à la première instruction située après le gestionnaire d'exceptions.

Une déclaration **goto** peut également sauter hors de la section gardée, et il ne dégrade pas les performances comme il le fait dans une déclaration **d’essai-enfin.** C’est parce que le dénouement de la pile ne se produit pas. Cependant, nous vous recommandons d’utiliser le mot clé **__leave** plutôt **qu’une déclaration goto.** La raison en est que vous êtes moins susceptible de faire une erreur de programmation si la section gardée est grande ou complexe.

### <a name="structured-exception-handling-intrinsic-functions"></a>Fonctions intrinsèques de gestion structurée des exceptions

La manipulation structurée des exceptions fournit deux fonctions intrinsèques qui sont disponibles à l’utilisation avec **l’énoncé try-except** : [GetExceptionCode](/windows/win32/Debug/getexceptioncode) et [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`retourne le code (un intégré 32 bits) de l’exception.

La fonction `GetExceptionInformation` intrinsèque renvoie un pointeur à une structure [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) contenant des informations supplémentaires sur l’exception. Ce pointeur vous permet d'accéder à l'état de l'ordinateur qui existait au moment d'une exception matérielle. La structure est comme suit :

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Les types `PEXCEPTION_RECORD` `PCONTEXT` de pointeurs et \<sont définis dans le `_EXCEPTION_RECORD` fichier `_CONTEXT` inclure winnt.h>, et sont définis dans le fichier \<inclure excpt.h>

Vous pouvez `GetExceptionCode` utiliser dans le gestionnaire d’exception. Cependant, vous `GetExceptionInformation` ne pouvez utiliser que dans l’expression du filtre d’exception. Les informations qu’il indique sont généralement sur la pile et ne sont plus disponibles lorsque le contrôle est transféré au gestionnaire d’exception.

La fonction intrinsèque [AbnormalTermination](/windows/win32/Debug/abnormaltermination) est disponible au sein d’un gestionnaire de terminaison. Il renvoie 0 si le corps de la déclaration **d’essai-enfin** se termine séquentiellement. Dans tous les autres cas, elle retourne 1.

\<excpt.h> définit quelques noms alternatifs pour ces intrinsèques :

`GetExceptionCode`est équivalent à`_exception_code`

`GetExceptionInformation`est équivalent à`_exception_info`

`AbnormalTermination`est équivalent à`_abnormal_termination`

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

[Rédaction d’un gestionnaire d’exception](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
