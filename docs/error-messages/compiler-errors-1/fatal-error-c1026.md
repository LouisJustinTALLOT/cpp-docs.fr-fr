---
title: Erreur irrécupérable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 9ea97bef16bebb8fc0e765ed708e54baee9a64de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220338"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026

dépassement de capacité de la pile de l'analyseur, programme trop complexe

L’espace requis pour analyser le programme a provoqué un dépassement de capacité de la pile du compilateur.

Réduisez la complexité des expressions en procédant comme suit :

- Diminution de l’imbrication dans **`for`** les **`switch`** instructions et. Placez des instructions plus profondément imbriquées dans des fonctions distinctes.

- Fractionnement des expressions longues qui impliquent des opérateurs virgules ou des appels de fonction.
