---
title: 2.6.2 Construction critical
ms.date: 11/04/2016
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
ms.openlocfilehash: dcc0e6144be5daee2a225cda621db818e5a38e2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539072"
---
# <a name="262-critical-construct"></a>2.6.2 Construction critical

Le **critique** directive identifie une construction qui limite l’exécution du bloc structuré associé à un seul thread à la fois. La syntaxe de la **critique** directive se présente comme suit :

```
#pragma omp critical [(name)]  new-linestructured-block
```

Facultatif *nom* peut être utilisé pour identifier la zone critique. Identificateurs utilisés pour identifier une zone critique ont une liaison externe et se trouvent dans un espace de noms qui diffèrent dans les espaces de noms utilisés par les étiquettes, les balises, les membres et les identificateurs ordinaires.

Un thread attend au début d’une zone critique aucun autre thread n’exécute une zone critique (n’importe où dans le programme) portant le même nom. Tous les sans nom **critique** directives mappent le même nom pas spécifié.