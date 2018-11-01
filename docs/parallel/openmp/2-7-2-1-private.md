---
title: 2.7.2.1 private
ms.date: 11/04/2016
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
ms.openlocfilehash: c1a2560eb80c848605698c435e3a0f0f7e66b75a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536953"
---
# <a name="2721-private"></a>2.7.2.1 private

Le `private` clause déclare les variables dans la liste de variable, être privée pour chaque thread dans une équipe. La syntaxe de la `private` clause se présente comme suit :

```
private(variable-list)
```

Le comportement d’une variable spécifiée dans un `private` clause se présente comme suit. Un nouvel objet avec une durée de stockage automatique est affectée pour la construction. La taille et l’alignement du nouvel objet sont déterminés par le type de la variable. Cette allocation se produit une fois pour chaque thread dans l’équipe, et un constructeur par défaut est appelé pour un objet de classe si nécessaire. Sinon, la valeur initiale est indéterminée.  L’objet d’origine référencé par la variable a une valeur indéterminée lors de l’entrée à la construction ne doit pas être modifiée dans l’étendue dynamique de la construction et a une valeur indéterminée la sortie de la construction.

Dans l’étendue lexicale de la construction de directive, la variable fait référence le nouvel objet privé alloué par le thread.

Les restrictions à le `private` clause sont les suivantes :

- Une variable avec un type de classe qui est spécifié dans un `private` clause doit avoir un constructeur par défaut accessible et non équivoque.

- Une variable spécifiée dans un `private` clause ne doit pas avoir un **const**-type qualifié, sauf si elle a une classe de type avec un `mutable` membre.

- Une variable spécifiée dans un `private` clause ne doit pas avoir un type incomplet ou un type référence.

- Variables qui apparaissent dans le `reduction` clause d’une **parallèles** directive ne peut pas être spécifiée dans un `private` clause sur une directive de partage de travail qui est liée à la construction parallèle.