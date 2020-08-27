---
title: try-except, instruction (C)
description: Microsoft C/C++ implémente la gestion structurée des exceptions (SEH) à l’aide d’une extension de langage d’instruction try-except.
ms.date: 08/24/2020
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: e327150431fef3384f2b98940939444b2e6d96ea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898725"
---
# <a name="try-except-statement-c"></a>try-except, instruction (C)

**Spécifique à Microsoft**

L' `try-except` instruction est une extension Microsoft du langage C qui permet aux applications de prendre le contrôle d’un programme lorsque des événements qui terminent normalement l’exécution se produisent. Ces événements sont appelés « exceptions » et le mécanisme de gestion des exceptions s'appelle « gestion structurée des exceptions ».

Il peut s’agir d’exceptions matérielles ou logicielles. Même lorsque les applications ne peuvent pas complètement récupérer à partir d’exceptions matérielles ou logicielles, la gestion structurée des exceptions permet d’enregistrer et d’afficher des informations sur les erreurs. Il est utile d’intercepter l’état interne de l’application pour aider à diagnostiquer le problème. En particulier, il est utile pour les problèmes intermittents qui ne sont pas faciles à reproduire.

## <a name="syntax"></a>Syntaxe

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

L’instruction composée après la **`__try`** clause est la *section protégée*. L’instruction composée après la **`__except`** clause est le *Gestionnaire d’exceptions*. Le gestionnaire spécifie un ensemble d’actions à entreprendre si une exception est levée pendant l’exécution de la section protégée. L'exécution se déroule comme suit :

1. La section protégée est exécutée.

1. Si aucune exception ne se produit pendant l’exécution de la section protégée, l’exécution se poursuit à l’instruction qui suit la **`__except`** clause.

1. Si une exception se produit pendant l’exécution de la section protégée ou dans une routine appelée par la section protégée, l' **`__except`** expression est évaluée. La valeur retournée détermine comment l’exception est gérée. Il existe trois valeurs possibles :

   - `EXCEPTION_CONTINUE_SEARCH`: L’exception n’est pas reconnue. Continuez à rechercher un gestionnaire dans la pile, tout d’abord pour contenir des `try-except` instructions, puis pour les gestionnaires avec la priorité la plus élevée suivante.

   - `EXCEPTION_CONTINUE_EXECUTION`: L’exception est reconnue mais ignorée. Poursuivre l'exécution au point où l'exception s'est produite.

   - `EXCEPTION_EXECUTE_HANDLER` L’exception est reconnue. Transférez le contrôle au gestionnaire d’exceptions en exécutant l' **`__except`** instruction composée, puis continuez l’exécution au point où l’exception s’est produite.

Étant donné que l' **`__except`** expression est évaluée comme une expression C, elle est limitée à une valeur unique, à l’opérateur d’expression conditionnelle ou à l’opérateur virgule. Si un traitement plus étendu est requis, l'expression peut appeler une routine qui retourne l'une des trois valeurs répertoriées ci-dessus.

> [!NOTE]
> La gestion structurée des exceptions fonctionne avec les fichiers sources C et C++. Toutefois, elle n’est pas conçue spécifiquement pour C++. Pour les programmes C++ portables, la gestion des exceptions C++ doit être utilisée à la place de la gestion structurée des exceptions. En outre, le mécanisme de gestion des exceptions C++ est beaucoup plus souple, car il peut gérer les exceptions de tout type. Pour plus d’informations, consultez [gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md) dans la référence du *langage C++*.

Chaque routine dans une application peut avoir son propre gestionnaire d'exceptions. L' **`__except`** expression s’exécute dans la portée du **`__try`** corps. Il a accès à toutes les variables locales déclarées ici.

Le **`__leave`** mot clé est valide dans un `try-except` bloc d’instructions. L’effet de **`__leave`** est d’accéder à la fin du `try-except` bloc. L'exécution reprend après la fin du gestionnaire d'exceptions. Bien qu’une **`goto`** instruction puisse être utilisée pour obtenir le même résultat, une **`goto`** instruction provoque le déroulement de la pile. L' **`__leave`** instruction est plus efficace car elle n’implique pas le déroulement de la pile.

Le fait de quitter une `try-except` instruction à l’aide de la `longjmp` fonction runtime est considéré comme un arrêt anormal. Il n’est pas légal de rentrer dans une **`__try`** instruction, mais il est légal d’en sortir un. Le gestionnaire d’exceptions n’est pas appelé si un processus est supprimé au milieu de l’exécution d’une `try-except` instruction.

## <a name="example"></a>Exemple

Voici un exemple de gestionnaire d’exceptions et de gestionnaire de terminaisons. Pour plus d’informations sur les gestionnaires de terminaisons, consultez [ `try-finally` Statement (C)](../c-language/try-finally-statement-c.md).

```C
.
.
.
puts("hello");
__try {
   puts("in try");
   __try {
      puts("in try");
      RAISE_AN_EXCEPTION();
   } __finally {
      puts("in finally");
   }
} __except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ) {
   puts("in except");
}
puts("world");
```

Voici la sortie de l’exemple, avec un Commentaire ajouté à droite :

```Output
hello
in try              /* fall into try                        */
in try              /* fall into nested try                 */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`try-except` instruction (C++)](../cpp/try-except-statement.md)
