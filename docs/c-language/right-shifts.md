---
title: Décalages vers la droite
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: 4b83aa231e6e7904fe5682b32a861ffe301b9747
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199410"
---
# <a name="right-shifts"></a>Décalages vers la droite

Résultat d'un décalage vers la droite d'un type intégral signé de valeur négative

Le décalage d'une valeur négative vers la droite produit la moitié de la valeur absolue, arrondie à la valeur inférieure. Par exemple, la **`signed short`** valeur-253 (hex 0xFF03, binary 11111111 00000011) décalée vers la droite d’un bit produit-127 (hex 0xFF81, binary 11111111 10000001). Une valeur 253 positive décalée vers la droite produit la valeur +126.

Le décalage vers la droite conserve le bit de signe des types intégraux signés. Lorsqu'un entier signé est décalé vers la droite, le bit le plus significatif reste défini. Par exemple, si 0xF0000000 est un signed **`int`** , un décalage vers la droite produit la valeur 0xf8000000. Le décalage d’une valeur négative de **`int`** 32 fois le produit 0xFFFFFFFF.

Lorsqu'un entier non signé est décalé vers la droite, le bits le plus significatif est effacé. Par exemple, si 0xF000 est non signé, le résultat est 0x7800. Le décalage d’une **`unsigned`** ou de **`int`** droite positive 32 fois génère 0x00000000.

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)
