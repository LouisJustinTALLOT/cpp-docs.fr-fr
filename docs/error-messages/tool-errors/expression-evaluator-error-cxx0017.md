---
title: Évaluateur d'expression, erreur CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602528"
---
# <a name="expression-evaluator-error-cxx0017"></a>Évaluateur d'expression, erreur CXX0017

symbole introuvable

Impossible de trouver un symbole spécifié dans une expression.

Une des causes possibles de cette erreur est une incompatibilité de cas dans le nom du symbole. Étant donné que C et C++ sont des langages de respect de la casse, un nom de symbole doit figurer dans la casse exacte dans laquelle il est défini dans la source.

Cette erreur peut se produire lorsque vous tentez de convertir une variable afin des pour regarder la variable pendant le débogage. Le `typedef` déclare un nouveau nom pour un type, mais il ne définit pas un nouveau type. La conversion de type tentée dans le débogueur requiert le nom d’un type défini.

Cette erreur est identique à CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Assurez-vous que le symbole est déjà déclaré au niveau du point du programme où il est utilisé.

1. Pour effectuer un cast de variables dans le débogueur, utilisez un nom de type réel plutôt qu’un `typedef`-nom défini.