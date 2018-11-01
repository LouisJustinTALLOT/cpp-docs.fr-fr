---
title: 2.7.2.3 lastprivate
ms.date: 11/04/2016
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
ms.openlocfilehash: 15f9af23c4f4e1c0ce2914a979f7a41e7b4a6bc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428456"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

Le `lastprivate` clause offre un sur-ensemble de la fonctionnalité fournie par le `private` clause. La syntaxe de la `lastprivate` clause se présente comme suit :

```
lastprivate(variable-list)
```

Variables spécifiées dans le *variable-list* ont `private` sémantique de la clause. Quand un `lastprivate` clause apparaît sur la directive qui identifie une construction de partage de travail, la valeur de chaque `lastprivate` à partir de la manière séquentielle dernière itération de la boucle associée, ou la directive de section lexicalement dernier, la variable est assignée à la objet d’origine de la variable. Une valeur assignée aux variables qui ne sont pas par la dernière itération de la **pour** ou **parallèles pour**, ou en la lexicalement la dernière section de la **sections** ou  **sections parallèles** directive, ont des valeurs indéterminées après la construction. Non affectés sous-objets ont également une valeur indéterminée après la construction.

Les restrictions à le `lastprivate` clause sont les suivantes :

- Toutes les restrictions pour `private` s’appliquent.

- Une variable avec un type de classe qui est spécifié comme `lastprivate` doit avoir un opérateur d’assignation de copie accessible et non équivoque.

- Variables qui sont privés au sein d’une région parallèle ou qui apparaissent dans le `reduction` clause d’une **parallèles** directive ne peut pas être spécifiée dans un `lastprivate` clause sur une directive de partage de travail qui est liée à la construction parallèle.