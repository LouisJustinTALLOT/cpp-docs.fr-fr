---
title: Erreur irrécupérable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666186"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026

dépassement de capacité de la pile de l'analyseur, programme trop complexe

L’espace requis pour analyser le programme a provoqué un dépassement de capacité de pile du compilateur.

Réduire la complexité des expressions en :

- Diminution de l’imbrication dans `for` et `switch` instructions. Placer des instructions plus profondément imbriquées dans des fonctions séparées.

- Découper des expressions longues qui impliquent des opérateurs de virgules ou des appels de fonction.