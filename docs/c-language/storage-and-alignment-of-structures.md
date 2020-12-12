---
description: 'En savoir plus sur : stockage et alignement de structures'
title: Stockage et alignement de structures
ms.date: 11/04/2016
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
ms.openlocfilehash: 8cffc3ddfcc868a7ccb727a5092e2389dbf016a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213687"
---
# <a name="storage-and-alignment-of-structures"></a>Stockage et alignement de structures

**Spécifique à Microsoft**

Les membres d'une structure sont stockés de manière séquentielle dans l'ordre dans lequel ils sont déclarés : le premier membre a l'adresse mémoire la plus basse et le dernier la plus élevée.

Chaque objet de données possède un *alignment-requirement*. Pour les structures, l’exigence est le membre le plus grand. Un *décalage* est alloué à chaque objet afin que

*décalage* `%` *alignement-exigence* `==` entre

Les champs de bits adjacents sont empaquetés dans la même unité d’allocation de 1, 2 ou 4 octets si les types intégraux sont de la même taille et si le champ de bits suivant s’insère dans l’unité d’allocation actuelle sans dépasser la limite imposée par les exigences d’alignement courantes des champs de bits.

Pour économiser l'espace ou se conformer aux structures de données existantes, vous pouvez stocker des structures de manière plus ou moins compacte. L’option du compilateur [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] et le [#pragma pack](../preprocessor/pack.md) contrôlent la façon dont les données de la structure sont « assemblées » en mémoire. Quand vous utilisez l’option /Zp[*n*], où *n* est 1, 2, 4, 8 ou 16, chaque membre de la structure après le premier est enregistré aux limites des octets qui représente la spécification d’alignement du champ ou la taille d’assemblage (*n*), selon celui qui est le plus petit. Les limites d'octets exprimées comme une formule sont

```
min( n, sizeof( item ) )
```

où *n* est la taille d’assemblage exprimée avec l’option /Zp[*n*] et *item* est le membre de la structure. La taille de compression par défaut est /Zp8.

Pour utiliser le pragma `pack` pour spécifier une compression autre que celle spécifiée sur la ligne de commande pour une structure particulière, indiquez le pragma `pack`, où la taille de compression est 1, 2, 4, 8 ou 16, avant la structure. Pour rétablir la compression donnée sur la ligne de commande, spécifiez le pragma `pack` sans argument.

Par défaut, les champs de bits sont dimensionnés **`long`** pour le compilateur Microsoft C. Les membres de la structure sont alignés sur la taille du type ou sur la taille de /Zp[*n*], selon celle qui est la plus petite. La taille par défaut est 4.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations de structure](../c-language/structure-declarations.md)
