---
title: Erreur du compilateur C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177389"
---
# <a name="compiler-error-c2585"></a>Erreur du compilateur C2585

la conversion explicite en’type’est ambiguë

La conversion de type peut produire plusieurs résultats.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Conversion à partir d’un type de classe ou de structure en fonction de l’héritage multiple. Si le type hérite plusieurs fois de la même classe de base, la fonction ou l’opérateur de conversion doit utiliser la résolution de portée (`::`) pour spécifier les classes héritées à utiliser dans la conversion.

1. Un opérateur de conversion et un constructeur ont été définis pour effectuer la même conversion.
