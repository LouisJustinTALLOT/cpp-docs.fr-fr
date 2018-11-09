---
title: Durée de vie
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 5e5d3b852148284312d2e1fb4cee1df432ac161b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665216"
---
# <a name="lifetime"></a>Durée de vie

La « durée de vie » est la période durant l'exécution d'un programme pendant laquelle une variable ou une fonction existe. La durée de stockage de l'identificateur détermine sa durée de vie.

Un identificateur déclaré avec le *storage-class-specifier* **static** possède une durée de stockage statique. Les identificateurs avec une durée de stockage statique (également appelés identificateurs « globaux ») ont un stockage et une valeur définie pendant toute la durée d'un programme. Le stockage est réservé et la valeur stockée de l'identificateur est initialisée une seule fois, avant le démarrage du programme. Un identificateur déclaré avec liaison externe ou interne a également une durée de stockage statique (consultez [Liaison](../c-language/linkage.md)).

Un identificateur déclaré sans spécificateur de classe de stockage **static** a une durée de stockage automatique s'il est déclaré dans une fonction. Un identificateur avec une durée de stockage automatique (un « identificateur local ») a un stockage et une valeur définie uniquement dans le bloc où il est défini ou déclaré. Un nouveau stockage est alloué à un identificateur automatique chaque fois que le programme accède à ce bloc, et il perd son stockage (et sa valeur) lorsque le programme quitte le bloc. Les identificateurs déclarés dans une fonction sans liaison ont également une durée de stockage automatique.

Les règles suivantes spécifient si un identificateur a une durée de vie globale (statique) ou locale (automatique) :

- Toutes les fonctions ont une durée de vie statique. Par conséquent, elles existent à tout moment pendant l'exécution du programme. Les identificateurs déclarés au niveau externe (autrement dit, en dehors de tous les blocs du programme au même niveau que les définitions de fonction) ont toujours une durée de vie globale (statique).

- Si une variable locale a un initialiseur, elle est initialisée chaque fois qu'elle est créée (sauf si elle est déclarée comme **static**). Les paramètres des fonctions ont également une durée de vie locale. Vous pouvez spécifier une durée de vie globale pour un identificateur dans un bloc en incluant le spécificateur de classe de stockage **static** dans sa déclaration. Une fois déclarée **static**, la variable conserve sa valeur d'une entrée du bloc à la suivante.

Bien qu'un identificateur à la durée de vie globale existe durant toute l'exécution du programme source (c'est le cas par exemple d'une variable déclarée de manière externe ou d'une variable locale déclarée avec le mot clé **static** ), il peut ne pas être visible dans toutes les parties du programme. Pour plus d'informations sur la visibilité, consultez [Portée et visibilité](../c-language/scope-and-visibility.md). Pour obtenir une discussion du non terminal [spécificateur-classe-stockage](../c-language/c-storage-classes.md), consultez *Classes de stockage*.

La mémoire peut être allouée en fonction des besoins (de manière dynamique) lorsqu'elle est créée par l'intermédiaire de routines de bibliothèque spéciales telles que `malloc`. Comme l'allocation dynamique de la mémoire utilise des routines de bibliothèque, cela n'est pas considéré comme faisant partie du langage. Consultez la fonction [malloc](../c-runtime-library/reference/malloc.md) dans la *Référence de la bibliothèque Runtime*.

## <a name="see-also"></a>Voir aussi

[Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md)