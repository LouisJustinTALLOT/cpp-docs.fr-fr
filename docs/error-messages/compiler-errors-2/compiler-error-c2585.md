---
description: 'En savoir plus sur : erreur du compilateur C2585'
title: Erreur du compilateur C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 568e5db1ca160b9fd13596d4f94f646cb4cf0bdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177651"
---
# <a name="compiler-error-c2585"></a>Erreur du compilateur C2585

la conversion explicite en’type’est ambiguë

La conversion de type peut produire plusieurs résultats.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Conversion à partir d’un type de classe ou de structure en fonction de l’héritage multiple. Si le type hérite plusieurs fois de la même classe de base, la fonction ou l’opérateur de conversion doit utiliser la résolution de portée ( `::` ) pour spécifier les classes héritées à utiliser dans la conversion.

1. Un opérateur de conversion et un constructeur ont été définis pour effectuer la même conversion.
