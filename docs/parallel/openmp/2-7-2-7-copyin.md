---
title: 2.7.2.7 copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94b4c529b7ad6fd717be1e1dee0edd3ff9ac3ff5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426885"
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