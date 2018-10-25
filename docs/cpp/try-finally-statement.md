---
title: Instruction try-finally | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4040f5a05f8c9bccfbf1c8b48a40188f684d48ad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060011"
---
# <a name="try-finally-statement"></a>try-finally, instruction

**Section spécifique à Microsoft**

La syntaxe suivante décrit la **try-finally** instruction :

```cpp
__try {
   // guarded code
}
__finally {
   // termination code
}
```

## <a name="grammar"></a>Grammaire

*try-finally-statement*: **__try** *compound-statement*

**__finally** *compound-statement*

Le **try-finally** instruction est une extension de Microsoft pour les langages C et C++ qui permet aux applications cibles garantir l’exécution de code de nettoyage lorsque l’exécution d’un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. Le **try-finally** instruction est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur qui peut entraîner prématuré de retour de la routine.

Pour plus d’informations et un exemple de code, consultez [essayez-EXCEPT, instruction](../cpp/try-except-statement.md). Pour plus d’informations sur structurée des exceptions en général, consultez [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Pour plus d’informations sur la gestion des exceptions dans les applications managées, consultez [gestion des exceptions sous /clr](../windows/exception-handling-cpp-component-extensions.md).

> [!NOTE]
>  La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour les programmes C++, il est recommandé d’utiliser le mécanisme de gestion des exceptions C++ ([try, catch et throw](../cpp/try-throw-and-catch-statements-cpp.md) instructions).

L’instruction composée après la **__try** clause est la section protégée. L’instruction composée après la **__finally** clause est le Gestionnaire de terminaisons. Le gestionnaire spécifie un jeu d'actions qui s'exécutent lorsque la section protégée est fermée, que la section protégée soit fermée par une exception (fin anormale) ou par un passage standard (fin normale).

Le contrôle atteint une **__try** instruction par exécution séquentielle simple (passage). Lorsque le contrôle pénètre dans le **__try**, son gestionnaire associé devient actif. Si le flux de contrôle atteint la fin du bloc try, l'exécution se produit de la façon suivante :

1. Le gestionnaire de terminaisons est appelé.

1. Lorsque le Gestionnaire de terminaisons est terminée, l’exécution se poursuit après le **__finally** instruction. Quelle que soit la façon dont la section protégée se termine (par exemple, via un **goto** hors du corps protégé ou un **retourner** instruction), le Gestionnaire de terminaisons est exécuté *avant* le flux de contrôle se déplace hors de la section protégée.

   Un **__finally** instruction ne bloque pas la recherche d’un gestionnaire d’exceptions approprié.

Si une exception se produit dans le **__try** bloc, le système d’exploitation doit rechercher un gestionnaire pour l’exception ou le programme échoue. Si un gestionnaire est trouvé, tous les **__finally** blocs sont exécutés et l’exécution reprend dans le gestionnaire.

Par exemple, supposons qu'une série d'appels de fonction lie la fonction A à la fonction D, comme indiqué dans l'illustration suivante. Chaque fonction a un gestionnaire de terminaisons. Si une exception est levée dans la fonction D et gérée dans A, les gestionnaires de terminaisons sont appelés dans l'ordre suivant à mesure que le système déroule la pile : D, C, B.

![Commande d’arrêt&#45;l’exécution du gestionnaire](../cpp/media/vc38cx1.gif "vc38CX1") ordre d’exécution de gestionnaire de terminaisons

> [!NOTE]
>  Le comportement de try-finally est différent d’autres langages qui prennent en charge l’utilisation de **enfin**, tel que c#.  Un seul **__try** peut-être, mais pas les deux de **__finally** et **__except**.  Si les deux doivent être utilisés conjointement, une instruction try-except externe doit entourer l'instruction try-finally interne.  Les règles qui spécifient le moment d'exécution de chaque blocs sont également différentes.

Pour assurer la compatibilité avec les versions précédentes, **_try**, **_finally**, et **_leave** sont synonymes de **__try**, **__ enfin**, et **__leave** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

## <a name="the-leave-keyword"></a>Mot clé __leave

Le **__leave** mot clé est valide uniquement dans la section protégée d’un **try-finally** instruction et son effet consiste à accéder à la fin de la section protégée. L'exécution continue à la première instruction dans le gestionnaire de terminaisons.

Un **goto** instruction peut également sortir de la section protégée, mais elle dégrade les performances, car elle appelle le déroulement de pile. Le **__leave** instruction est plus efficace, car elle n’entraîne pas le déroulement de pile.

## <a name="abnormal-termination"></a>Arrêt anormal

Quitter un **try-finally** à l’aide de l’instruction la [longjmp](../c-runtime-library/reference/longjmp.md) moment de l’exécution est considérée comme un arrêt anormal. Il n’est pas conforme de sauter dans une **__try** instruction mais conforme d’en sortir d’une. Tous les **__finally** instructions actives entre le point de départ (arrêt normal de la **__try** bloc) et la destination (le **__except** qui bloquent gère l’exception) doit être exécuté. Cela s'appelle un déroulement local.

Si un **essayez** bloc est terminé prématurément pour une raison quelconque, y compris un saut hors du bloc, le système exécute associé **enfin** bloc dans le cadre du processus de déroulement de la pile. Dans ce cas, le [AbnormalTermination](/windows/desktop/Debug/abnormaltermination) fonction renvoie **true** si elle est appelée depuis le **enfin** bloquer ; sinon, elle retourne **false**.

Le Gestionnaire de terminaisons n’est pas appelé si un processus est tué au milieu de l’exécution un **try-finally** instruction.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Syntaxe du Gestionnaire de terminaisons](/windows/desktop/Debug/termination-handler-syntax)