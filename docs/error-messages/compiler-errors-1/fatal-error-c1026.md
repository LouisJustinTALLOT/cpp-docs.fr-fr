---
title: Erreur irrécupérable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204651"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026

dépassement de capacité de la pile de l'analyseur, programme trop complexe

L’espace requis pour analyser le programme a provoqué un dépassement de capacité de la pile du compilateur.

Réduisez la complexité des expressions en procédant comme suit :

- Diminution de l’imbrication dans les instructions `for` et `switch`. Placez des instructions plus profondément imbriquées dans des fonctions distinctes.

- Fractionnement des expressions longues qui impliquent des opérateurs virgules ou des appels de fonction.
