---
title: Erreur du compilateur C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593256"
---
# <a name="compiler-error-c2585"></a>Erreur du compilateur C2585

une conversion explicite en 'type' est AMBIGUE

La conversion de type peut produire plusieurs résultats.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Conversion d’un type de classe ou structure basé sur l’héritage multiple. Si le type hérite de la classe de base même plusieurs fois, la fonction de conversion ou un opérateur doit utiliser la résolution de portée (`::`) de spécifier les classes héritées à utiliser dans la conversion.

1. Un opérateur de conversion et un constructeur définis effectue la même conversion.