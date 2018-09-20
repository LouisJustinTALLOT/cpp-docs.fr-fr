---
title: 2.4.2 construction sections | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ae940e37b40cbb9c883c4d7d6bca7b0fa65520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410544"
---
# <a name="242-sections-construct"></a>2.4.2 Construction sections

Le **sections** directive identifie une construction de partage de travail noniterative qui spécifie un ensemble de constructions qui doivent être divisée entre les threads dans une équipe. Chaque section est exécutée une fois par un thread dans l’équipe. La syntaxe de la **sections** directive se présente comme suit :

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La clause est une des opérations suivantes :

**privé (** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate (** *variable-list* **)**

**reduction(** *operator* **:**  *variable-list* **)**

**nowait**

Chaque section est précédée par un **section** directive, bien que le **section** directive est facultative pour la première section. Le **section** directives doivent apparaître dans l’étendue lexicale de la **sections** directive. Il existe une barrière implicite à la fin d’un **sections** construire, sauf si un **nowait** est spécifié.

Restrictions pour le **sections** directive sont les suivantes :

- Un **section** directive ne doit pas apparaître en dehors de l’étendue lexicale de la **sections** directive.

- Un seul **nowait** clause peut apparaître sur un **sections** directive.

## <a name="cross-references"></a>Références externes :

- **privé**, **firstprivate**, **lastprivate**, et **réduction** clauses, consultez [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.