---
title: 2.6.1 Construction master
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475528"
---
# <a name="261-master-construct"></a>2.6.1 Construction master

Le **master** directive identifie une construction qui spécifie un bloc structuré qui est exécuté par le thread principal de l’équipe. La syntaxe de la **master** directive se présente comme suit :

```
#pragma omp master new-linestructured-block
```

Autres threads dans l’équipe n’exécutent pas le bloc structuré associé. Il n’existe plus aucune barrière implicite sur entrée ou sortie à partir de la construction master.