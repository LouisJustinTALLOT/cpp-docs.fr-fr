---
title: try-finally, instruction
description: Référence Microsoft C++ aux instructions de gestion des exceptions structurées en __try et __finally.
ms.date: 08/25/2020
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: edabbbe35c86f0305e31f36584c4dfe01f2f88cd
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898646"
---
# <a name="try-finally-statement"></a>Instruction `try-finally`

L' `try-finally` instruction est une extension **spécifique à Microsoft** qui prend en charge la gestion structurée des exceptions dans les langages C et C++.

## <a name="syntax"></a>Syntaxe

La syntaxe suivante décrit l' `try-finally` instruction :

```cpp
    // . . .
    __try {
        // guarded code
    }
    __finally {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>Grammaire

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

L' `try-finally` instruction est une extension Microsoft des langages C et C++ qui permet aux applications cibles de garantir l’exécution du code de nettoyage lorsque l’exécution d’un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. L'instruction `try-finally` est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur qui peut provoquer un retour prématuré de la routine.

Pour obtenir des informations connexes et un exemple de code, consultez [ `try-except` instruction](../cpp/try-except-statement.md). Pour plus d’informations sur la gestion structurée des exceptions en général, consultez [gestion structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md). Pour plus d’informations sur la gestion des exceptions dans les applications managées avec C++/CLI, consultez [gestion des exceptions sous `/clr` ](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes c++, il est recommandé d’utiliser le mécanisme de gestion des exceptions C++ (instructions[ `try` , `catch` , et `throw` ](../cpp/try-throw-and-catch-statements-cpp.md) ).

L’instruction composée après la **`__try`** clause est la section protégée. L’instruction composée après la **`__finally`** clause est le gestionnaire de terminaisons. Le gestionnaire spécifie un ensemble d’actions qui s’exécutent lorsque la section protégée est fermée, qu’elle quitte la section protégée par une exception (fin anormale) ou par un passage standard (fin normale).

Le contrôle atteint une **`__try`** instruction par exécution séquentielle simple (passage). Lorsque le contrôle entre dans **`__try`** , son gestionnaire associé devient actif. Si le flux de contrôle atteint la fin du bloc try, l'exécution se produit de la façon suivante :

1. Le gestionnaire de terminaisons est appelé.

1. Une fois le gestionnaire de terminaisons terminé, l’exécution se poursuit après l' **`__finally`** instruction. Toutefois, la section protégée se termine (par exemple, par **`goto`** le biais d’un corps protégé ou d’une **`return`** instruction), le gestionnaire de terminaisons est exécuté *avant que* le déroulement du contrôle ne quitte la section protégée.

   Une **`__finally`** instruction ne bloque pas la recherche d’un gestionnaire d’exceptions approprié.

Si une exception se produit dans le **`__try`** bloc, le système d’exploitation doit trouver un gestionnaire pour l’exception ou le programme échoue. Si un gestionnaire est trouvé, tous les blocs et tous **`__finally`** sont exécutés et l’exécution reprend dans le gestionnaire.

Par exemple, supposons qu'une série d'appels de fonction lie la fonction A à la fonction D, comme indiqué dans l'illustration suivante. Chaque fonction a un gestionnaire de terminaisons. Si une exception est levée dans la fonction D et gérée dans A, les gestionnaires de terminaisons sont appelés dans l'ordre suivant à mesure que le système déroule la pile : D, C, B.

![Ordre d’arrêt de l’exécution du gestionnaire de&#45;](../cpp/media/vc38cx1.gif "Ordre d’arrêt de l’exécution du gestionnaire de&#45;") <br/>
Fin de l'ordre d'exécution du gestionnaire

> [!NOTE]
> Le comportement de try-finally est différent de celui des autres langages qui prennent en charge l’utilisation de **`finally`** , tels que C#.  Un seul **`__try`** peut avoir, mais pas les deux, de **`__finally`** et **`__except`** .  Si les deux doivent être utilisés conjointement, une instruction try-except externe doit entourer l'instruction try-finally interne.  Les règles qui spécifient le moment d'exécution de chaque blocs sont également différentes.

Pour la compatibilité avec les versions précédentes, **`_try`** , **`_finally`** et **`_leave`** sont des synonymes de **`__try`** , **`__finally`** et **`__leave`** sauf si l’option [ `/Za` de compilateur (désactivation des extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="the-__leave-keyword"></a>Mot clé __leave

Le **`__leave`** mot clé est valide uniquement dans la section protégée d’une `try-finally` instruction, et son effet est d’accéder à la fin de la section protégée. L'exécution continue à la première instruction dans le gestionnaire de terminaisons.

Une **`goto`** instruction peut également sortir de la section protégée, mais elle dégrade les performances car elle appelle le déroulement de la pile. L' **`__leave`** instruction est plus efficace, car elle ne provoque pas le déroulement de la pile.

## <a name="abnormal-termination"></a>Arrêt anormal

La sortie d’une `try-finally` instruction à l’aide de la fonction runtime [longjmp](../c-runtime-library/reference/longjmp.md) est considérée comme un arrêt anormal. Il n’est pas légal de rentrer dans une **`__try`** instruction, mais il est légal d’en sortir un. Toutes les **`__finally`** instructions qui sont actives entre le point de départ (fin normale du **`__try`** bloc) et la destination (le **`__except`** bloc qui gère l’exception) doivent être exécutées. Il s’agit d’un *déroulement local*.

Si un **`__try`** bloc se termine prématurément pour une raison quelconque, y compris un saut hors du bloc, le système exécute le bloc associé **`__finally`** dans le cadre du processus de déroulement de la pile. Dans ce cas, la [`AbnormalTermination`](/windows/win32/Debug/abnormaltermination) fonction retourne **`true`** si elle est appelée à partir du **`__finally`** bloc ; sinon, elle retourne **`false`** .

Le gestionnaire de terminaisons n’est pas appelé si un processus est supprimé au milieu de l’exécution d’une `try-finally` instruction.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire des arrêts](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Syntaxe du gestionnaire de terminaisons](/windows/win32/Debug/termination-handler-syntax)
