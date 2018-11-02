---
title: 2.7.1 Directive threadprivate
ms.date: 11/04/2016
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
ms.openlocfilehash: 0ba5ea4892d70458f0f63bcb5b92968b36235273
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647003"
---
# <a name="271-threadprivate-directive"></a>2.7.1 Directive threadprivate

Le `threadprivate` directive rend la portée de fichier nommée, portée de l’espace de noms ou des variables statiques de portée de bloc spécifiés dans le *variable-list* privé à un thread. *liste de la variable* est une liste séparée par des virgules de variables qui n’ont pas un type incomplet. La syntaxe de la `threadprivate` directive se présente comme suit :

```
#pragma omp threadprivate(variable-list) new-line
```

Chaque copie d’un `threadprivate` variable est initialisée une seule fois, à un point non spécifié dans le programme avant la première référence à cette copie et de la manière habituelle (par exemple, comme la copie principale serait initialisée dans une exécution en série du programme). Notez que si un objet est référencé dans un initialiseur explicit d’un `threadprivate` variable et la valeur de l’objet est modifié avant la première référence à une copie de la variable, puis le comportement n’est pas spécifié.

Comme avec n’importe quelle variable privée, un thread ne doit pas référencer copie d’un autre thread d’un `threadprivate` objet. Au cours de la série régions et les régions principales du programme, les références seront à la copie du thread principal de l’objet.

Après l’exécution de la première région parallèle, les données dans le `threadprivate` persistent uniquement si la dynamique threads mécanisme a été désactivée et si le nombre de threads reste inchangé pour toutes les régions parallèles des objets est garantie.

Les restrictions à le `threadprivate` directive sont les suivantes :

- Un `threadprivate` directive pour les variables de portée de fichier ou de la portée de l’espace de noms doit apparaître en dehors de toute définition ou la déclaration et doit précéder lexicalement toutes les références aux variables dans sa liste.

- Chaque variable dans le *variable-list* d’un `threadprivate` directive à la portée de fichier ou un espace de noms doit faire référence à une déclaration de variable à la portée de fichier ou un espace de noms qui précède lexicalement la directive.

- Un `threadprivate` directive pour les variables de portée de bloc statique doit apparaître dans la portée de la variable et non dans une étendue imbriquée. La directive doit précéder lexicalement toutes les références aux variables dans sa liste.

- Chaque variable dans le *variable-list* d’un `threadprivate` directive dans la portée de bloc doit faire référence à une déclaration de variable dans la même portée lexicale précédant la directive. La déclaration de variable doit utiliser le spécificateur de classe de stockage statique.

- Si une variable est spécifiée dans un `threadprivate` directive dans une unité de traduction, il doit être spécifié dans un `threadprivate` directive dans chaque unité de traduction dans laquelle elle est déclarée.

- Un `threadprivate` variable ne doit pas apparaître dans une clause à l’exception de la `copyin`, `copyprivate`, `schedule`, `num_threads`, ou le **si** clause.

- L’adresse d’un `threadprivate` variable n’est pas une constante d’adresse.

- A `threadprivate` variable ne doit pas avoir un type incomplet ou un type référence.

- A `threadprivate` variable de type de classe non POD doit avoir un constructeur de copie accessible et non équivoque si elle est déclarée avec un initialiseur explicit.

L’exemple suivant illustre comment la modification d’une variable qui s’affiche dans un initialiseur peut provoquer comportement non spécifié et également comment éviter ce problème à l’aide d’un objet auxiliaire et un constructeur de copie.

```
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

## <a name="cross-references"></a>Références externes :

- Threads dynamiques, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.

- `OMP_DYNAMIC` voir variable d’environnement [Section 4.3](../../parallel/openmp/4-3-omp-dynamic.md) page 49.