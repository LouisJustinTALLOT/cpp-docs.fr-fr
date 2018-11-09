---
title: Décalages vers la droite
ms.date: 11/04/2016
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
ms.openlocfilehash: f39c1f2f49f5a8a1f3bb5eb3f21736eedf32077e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518207"
---
# <a name="right-shifts"></a>Décalages vers la droite

Résultat d'un décalage vers la droite d'un type intégral signé de valeur négative

Le décalage d'une valeur négative vers la droite produit la moitié de la valeur absolue, arrondie à la valeur inférieure. Par exemple, une valeur `short` signée de -253 (0xFF03 en hexadécimal, 11111111 00000011 en binaire) décalée vers la droite d’un bit produit la valeur -127 (0xFF81 en hexadécimal, 11111111 10000001 en binaire). Une valeur 253 positive décalée vers la droite produit la valeur +126.

Le décalage vers la droite conserve le bit de signe des types intégraux signés. Lorsqu'un entier signé est décalé vers la droite, le bit le plus significatif reste défini. Par exemple, si 0xF0000000 est signé `int`, un décalage vers la droite génère la valeur 0xF8000000. Le décalage d'un `int` négatif vers la droite 32 fois génère la valeur 0xFFFFFFFF.

Lorsqu'un entier non signé est décalé vers la droite, le bits le plus significatif est effacé. Par exemple, si 0xF000 est non signé, le résultat est 0x7800. Le décalage d'un `unsigned` ou d'un `int` positif vers la droite 32 fois génère 0x00000000.

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)