---
title: try-finally, instruction
ms.date: 11/19/2018
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
ms.openlocfilehash: c26b72f7c675a4130f38c515cf71ecc290328ccc
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "69498604"
---
# <a name="try-finally-statement"></a>try-finally, instruction

**Section spécifique de Microsoft**

La syntaxe suivante décrit l’instruction **try-finally** :

> **\_ \_try**<br/>
> {<br/>
> &nbsp; &nbsp; &nbsp; &nbsp;//code protégé<br/>
> }<br/>
> **\_ \_finally**<br/>
> {<br/>
> &nbsp; &nbsp; &nbsp; &nbsp;//code d’arrêt<br/>
> }

## <a name="grammar"></a>Grammaire

*try-finally-statement* :<br/>
&nbsp; &nbsp; &nbsp; &nbsp; **\_** \_try *composée-instruction* **\_ 0finally** *composée-Statement*

L’instruction **try-finally** est une extension Microsoft du langage C C++ et des langages qui permet aux applications cibles de garantir l’exécution du code de nettoyage lorsque l’exécution d’un bloc de code est interrompue. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. L’instruction **try-finally** est particulièrement utile pour les routines qui ont plusieurs endroits où un contrôle est effectué pour une erreur susceptible de provoquer un retour prématuré de la routine.

Pour obtenir des informations connexes et un exemple de code, consultez [instruction try-except](../cpp/try-except-statement.md). Pour plus d’informations sur la gestion structurée des exceptions en général, consultez [gestion structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md). Pour plus d’informations sur la gestion des exceptions dans C++les applications managées avec/CLI, consultez [gestion des exceptions sous/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. Pour C++ les programmes, il est recommandé d’utiliser le C++ mécanisme de gestion des exceptions (instructions[try, catch et Throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

L’instruction composée après la clause **_ _ try** est la section protégée. L’instruction composée après la clause **_ _ finally** est le gestionnaire de terminaisons. Le gestionnaire spécifie un jeu d'actions qui s'exécutent lorsque la section protégée est fermée, que la section protégée soit fermée par une exception (fin anormale) ou par un passage standard (fin normale).

Le contrôle atteint une instruction **_ _ try** par exécution séquentielle simple (passage). Lorsque le contrôle entre dans l' **_ _ try**, son gestionnaire associé devient actif. Si le flux de contrôle atteint la fin du bloc try, l'exécution se produit de la façon suivante :

1. Le gestionnaire de terminaisons est appelé.

1. Lorsque le gestionnaire de terminaisons se termine, l’exécution se poursuit après l’instruction **_ _ finally** . Quelle que soit la façon dont la section protégée se termine (par exemple, via une instruction **goto** dans le corps protégé ou une instruction **Return** ), le gestionnaire de terminaisons est exécuté *avant que* le déroulement du contrôle ne quitte la section protégée.

   Une instruction **_ _ finally** ne bloque pas la recherche d’un gestionnaire d’exceptions approprié.

Si une exception se produit dans le bloc **_ _ try** , le système d’exploitation doit trouver un gestionnaire pour l’exception ou le programme va échouer. Si un gestionnaire est trouvé, tous les blocs **_ _ finally** sont exécutés et l’exécution reprend dans le gestionnaire.

Par exemple, supposons qu'une série d'appels de fonction lie la fonction A à la fonction D, comme indiqué dans l'illustration suivante. Chaque fonction a un gestionnaire de terminaisons. Si une exception est levée dans la fonction D et gérée dans A, les gestionnaires de terminaisons sont appelés dans l'ordre suivant à mesure que le système déroule la pile : D, C, B.

![Ordre d’exécution&#45;du gestionnaire de terminaisons](../cpp/media/vc38cx1.gif "Ordre d’exécution&#45;du gestionnaire de terminaisons") <br/>
Fin de l'ordre d'exécution du gestionnaire

> [!NOTE]
> Le comportement de try-finally est différent de celui des autres langages qui prennent en charge l’utilisation C#de **finally**, tels que.  Un seul **_ _ try** peut avoir, mais pas les deux, **_ _ finally** et **_ _ except**.  Si les deux doivent être utilisés conjointement, une instruction try-except externe doit entourer l'instruction try-finally interne.  Les règles qui spécifient le moment d'exécution de chaque blocs sont également différentes.

Pour la compatibilité avec les versions antérieures, **_try**, **_finally**et **_leave** sont des synonymes pour **_ _ try**, **_ _ final**et **__leave** sauf si l’option de compilateur [/za \(Disable les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est prescrit.

## <a name="the-__leave-keyword"></a>Mot clé __leave

Le mot clé **__leave** est valide uniquement dans la section protégée d’une instruction **try-finally** , et son effet est d’accéder à la fin de la section protégée. L'exécution continue à la première instruction dans le gestionnaire de terminaisons.

Une instruction **goto** peut également sortir de la section protégée, mais elle dégrade les performances car elle appelle le déroulement de la pile. L’instruction **__leave** est plus efficace, car elle ne provoque pas le déroulement de la pile.

## <a name="abnormal-termination"></a>Arrêt anormal

La sortie d’une instruction **try-finally** à l’aide de la fonction runtime [longjmp](../c-runtime-library/reference/longjmp.md) est considérée comme un arrêt anormal. Il n’est pas non plus possible d’accéder à une instruction **_ _ try** , mais d’en sortir une. Toutes les instructions **_ _ finally** qui sont actives entre le point de départ (fin normale du bloc **_ try** ) et la destination (le bloc **_ _ except** qui gère l’exception) doivent être exécutées. Cela s'appelle un déroulement local.

Si un bloc **try** s’arrête prématurément pour une raison quelconque, y compris un saut hors du bloc, le système exécute le bloc **finally** associé dans le cadre du processus de déroulement de la pile. Dans ce cas, la fonction [AbnormalTermination](/windows/win32/Debug/abnormaltermination) retourne **true** si elle est appelée depuis le bloc **finally** ; Sinon, elle retourne **false**.

Le gestionnaire de terminaisons n’est pas appelé si un processus est supprimé au milieu de l’exécution d’une instruction **try-finally** .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Syntaxe du gestionnaire de terminaisons](/windows/win32/Debug/termination-handler-syntax)