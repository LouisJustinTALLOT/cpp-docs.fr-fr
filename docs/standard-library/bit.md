---
title: '&lt;bit&gt;'
description: Fonctions permettant d’accéder, de manipuler et de traiter des bits individuels et des séquences de bits.
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: 5652d0af767520710ee08b1827e0df27c477ee6d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040052"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

Définit des fonctions pour accéder, manipuler et traiter des bits et des séquences de bits individuels.

Par exemple, il existe des fonctions permettant de faire pivoter des bits, de rechercher le nombre de bits définis ou désactivés consécutifs, de voir si un nombre est une puissance intégrale de deux, de rechercher le plus petit nombre de bits pour représenter un nombre, et ainsi de suite.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<bit>

**Espace de noms :** std

[/std : c + + latest](../build/reference/std-specify-language-standard-version.md) est requis.

## <a name="members"></a>Membres

### <a name="types"></a>Types

| Type | Description |
|--------|----------|
| [faible](bit-enum.md) | Spécifie le endianness de types scalaires. |

### <a name="functions"></a>Fonctions

| Fonction | Description |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | Réinterpréter la représentation de l’objet d’un type à un autre. |
|[bit_ceil](bit-functions.md#bit_ceil) | Recherche la plus petite puissance de deux supérieure ou égale à une valeur. |
|[bit_floor](bit-functions.md#bit_floor) | Recherche la puissance entière la plus grande de deux non supérieures à une valeur. |
|[bit_width](bit-functions.md#bit_width) | Recherche le plus petit nombre de bits nécessaires pour représenter une valeur. |
|[countl_zero](bit-functions.md#countl_zero) | Comptez le nombre de bits consécutifs définis sur zéro, en partant du bit le plus significatif. |
|[countl_one](bit-functions.md#countl_one) | Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le plus significatif. |
|[countr_zero](bit-functions.md#countr_zero) | Comptez le nombre de bits consécutifs définis sur zéro, à partir du bit le moins significatif. |
|[countr_one](bit-functions.md#countl_one) | Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le moins significatif. |
|[has_single_bit](bit-functions.md#has_single_bit) | Vérifiez si une valeur n’a qu’un seul bit défini sur un. Cela revient à tester si une valeur est une puissance de deux. |
|[popcount](bit-functions.md#popcount) | Comptez le nombre de bits définis sur un. |
|[rotl](bit-functions.md#rotl) | Calcule le résultat d’une rotation vers la gauche au niveau du bit. |
|[rotr](bit-functions.md#rotr) | Calcule le résultat d’une rotation vers la droite au niveau du bit. |

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](cpp-standard-library-header-files.md)