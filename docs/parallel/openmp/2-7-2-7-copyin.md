---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 65bb8faba085e5582e779fa0e9d5bf1a91a39f0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545442"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin

Le **copyin** clause fournit un mécanisme pour affecter la même valeur pour **threadprivate** variables pour chaque thread dans l’équipe de l’exécution de la région parallèle. Pour chaque variable spécifiée dans un **copyin** clause, la valeur de la variable dans le thread principal de l’équipe est copié, comme si, par assignation, dans les copies privées de thread au début de la région parallèle. La syntaxe de la **copyin** clause se présente comme suit :

```

copyin(
variable-list
)

```

Les restrictions à le **copyin** clause sont les suivantes :

- Une variable qui est spécifiée dans le **copyin** clause doit avoir un opérateur d’assignation de copie accessible et non équivoque.

- Une variable qui est spécifiée dans le **copyin** clause doit être un **threadprivate** variable.