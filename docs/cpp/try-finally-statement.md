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
ms.openlocfilehash: 045d2bf5617c81bcc4d7a202f36b112d5f0142a6
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246301"
---
# <a name="try-finally-statement"></a>try-finally, instruction

**Section spécifique de Microsoft**

The following syntax describes the **try-finally** statement:

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// guarded code<br/>
> }<br/>
> **\_\_finally**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// termination code<br/>
> }

## <a name="grammar"></a>Grammaire

*try-finally-statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\_\_try** *compound-statement* **\_\_finally** *compound-statement*

The **try-finally** statement is a Microsoft extension to the C and C++ languages that enables target applications to guarantee execution of cleanup code when execution of a block of code is interrupted. Le nettoyage se compose de tâches telles que la désallocation de mémoire, la fermeture de fichiers et la libération des handles de fichiers. The **try-finally** statement is especially useful for routines that have several places where a check is made for an error that could cause premature return from the routine.

For related information and a code sample, see [try-except Statement](../cpp/try-except-statement.md). For more information on structured exception handling in general, see [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). For more information on handling exceptions in managed applications with C++/CLI, see [Exception Handling under /clr](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec Win32 pour les fichiers sources C et C++. Toutefois, elle n'est pas conçue spécifiquement pour C++. Vous pouvez vous assurer que votre code est plus portable en utilisant la gestion des exceptions C++. En outre, la gestion des exceptions C++ est plus souple, car elle permet de traiter des exceptions de tout type. For C++ programs, it is recommended that you use the C++ exception-handling mechanism ([try, catch, and throw](../cpp/try-throw-and-catch-statements-cpp.md) statements).

The compound statement after the **__try** clause is the guarded section. The compound statement after the **__finally** clause is the termination handler. Le gestionnaire spécifie un jeu d'actions qui s'exécutent lorsque la section protégée est fermée, que la section protégée soit fermée par une exception (fin anormale) ou par un passage standard (fin normale).

Control reaches a **__try** statement by simple sequential execution (fall through). When control enters the **__try**, its associated handler becomes active. Si le flux de contrôle atteint la fin du bloc try, l'exécution se produit de la façon suivante :

1. Le gestionnaire de terminaisons est appelé.

1. When the termination handler completes, execution continues after the **__finally** statement. Regardless of how the guarded section ends (for example, via a **goto** out of the guarded body or a **return** statement), the termination handler is executed *before* the flow of control moves out of the guarded section.

   A **__finally** statement does not block searching for an appropriate exception handler.

If an exception occurs in the **__try** block, the operating system must find a handler for the exception or the program will fail. If a handler is found, any and all **__finally** blocks are executed and execution resumes in the handler.

Par exemple, supposons qu'une série d'appels de fonction lie la fonction A à la fonction D, comme indiqué dans l'illustration suivante. Chaque fonction a un gestionnaire de terminaisons. Si une exception est levée dans la fonction D et gérée dans A, les gestionnaires de terminaisons sont appelés dans l'ordre suivant à mesure que le système déroule la pile : D, C, B.

![Order of termination&#45;handler execution](../cpp/media/vc38cx1.gif "Order of termination&#45;handler execution") <br/>
Fin de l'ordre d'exécution du gestionnaire

> [!NOTE]
> The behavior of try-finally is different from some other languages that support the use of **finally**, such as C#.  A single **__try** may have either, but not both, of **__finally** and **__except**.  Si les deux doivent être utilisés conjointement, une instruction try-except externe doit entourer l'instruction try-finally interne.  Les règles qui spécifient le moment d'exécution de chaque blocs sont également différentes.

For compatibility with previous versions, **_try**, **_finally**, and **_leave** are synonyms for **__try**, **__finally**, and **__leave** unless compiler option [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) is specified.

## <a name="the-__leave-keyword"></a>Mot clé __leave

The **__leave** keyword is valid only within the guarded section of a **try-finally** statement, and its effect is to jump to the end of the guarded section. L'exécution continue à la première instruction dans le gestionnaire de terminaisons.

A **goto** statement can also jump out of the guarded section, but it degrades performance because it invokes stack unwinding. The **__leave** statement is more efficient because it does not cause stack unwinding.

## <a name="abnormal-termination"></a>Arrêt anormal

Exiting a **try-finally** statement using the [longjmp](../c-runtime-library/reference/longjmp.md) run-time function is considered abnormal termination. It is illegal to jump into a **__try** statement, but legal to jump out of one. All **__finally** statements that are active between the point of departure (normal termination of the **__try** block) and the destination (the **__except** block that handles the exception) must be run. Cela s'appelle un déroulement local.

If a **try** block is prematurely terminated for any reason, including a jump out of the block, the system executes the associated **finally** block as a part of the process of unwinding the stack. In such cases, the [AbnormalTermination](/windows/win32/Debug/abnormaltermination) function returns **true** if called from within the **finally** block; otherwise, it returns **false**.

The termination handler is not called if a process is killed in the middle of executing a **try-finally** statement.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Termination-Handler Syntax](/windows/win32/Debug/termination-handler-syntax)