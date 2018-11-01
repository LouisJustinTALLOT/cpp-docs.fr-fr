---
title: 2.4.3 Construction simple
ms.date: 11/04/2016
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
ms.openlocfilehash: 7dda98ee83ee08adc29830a9c4ada71a208705fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466363"
---
# <a name="243-single-construct"></a>2.4.3 Construction simple

Le **unique** directive identifie une construction qui spécifie que le bloc structuré associé est exécuté par un seul thread dans l’équipe (pas nécessairement le thread principal). La syntaxe de la **unique** directive se présente comme suit :

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La clause est une des opérations suivantes :

**privé (** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**copyprivate (** *variable-list* **)**

**nowait**

Il existe une barrière implicite après le **unique** construire, sauf si un **nowait** clause est spécifiée.

Restrictions pour le **unique** directive sont les suivantes :

- Un seul **nowait** clause peut apparaître sur un **unique** directive.

- Le **copyprivate** clause ne doit pas être utilisée avec le **nowait** clause.

## <a name="cross-references"></a>Références externes :

- **privé**, **firstprivate**, et **copyprivate** clauses, consultez [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.