---
title: Agrégats et Unions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aac6da94a0786e5cdc2eee4d16f5927f66e0a8d5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861185"
---
# <a name="aggregates-and-unions"></a>Agrégats et unions

Autres types, tels que des tableaux, des structs et unions, ont des exigences plus strictes de l’alignement qui garantissent la cohérence agrégée et union stockage et extraction des données. Voici les définitions de tableau, de structure et d’union :

- Tableau

   Contient un groupe ordonné d’objets de données adjacents. Chaque objet est appelé un élément. Tous les éléments dans un tableau ont la même taille et type de données.

- Structure

   Contient un groupe ordonné d’objets de données. Contrairement aux éléments d’un tableau, les objets de données au sein d’une structure peuvent avoir des tailles et types de données différents. Chaque objet de données dans une structure est appelé membre.

- Union

   Objet qui contient l’un d’un jeu de membres nommés. Les membres du jeu nommé peuvent être de n’importe quel type. Le stockage alloué pour une union est égal au stockage requis pour le plus grand membre de cette union, plus tout remplissage requis pour l’alignement.

Le tableau suivant présente l’alignement vivement recommandé pour les membres scalaires des unions et des structures.

||||
|-|-|-|
|Type scalaire|Type de données C|Alignement requis|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**unsigned short**|Word|
|**INT32**|**int**, **long**|Mot double|
|**UINT32**|**unsigned int, unsigned long**|Mot double|
|**INT64**|**__int64**|Mot quadruple|
|**UINT64**|**unsigned __int64**|Mot quadruple|
|**FP32 (simple précision)**|**float**|Mot double|
|**FP64 (double précision)**|**double**|Mot quadruple|
|**POINTEUR**|<strong>\*</strong>|Mot quadruple|
|**__m64**|**__m64 de struct**|Mot quadruple|
|**__m128**|**__m128 de struct**|Octaword|

Les règles d’alignement d’agrégation suivantes s’appliquent :

- L’alignement d’un tableau est le même que l’alignement d’un des éléments du tableau.

- L’alignement du début d’une structure ou une union est l’alignement maximale de tous les membres individuels. Chaque membre au sein de la structure ou union doit être placé à son propre alignement comme défini dans le tableau précédent, ce qui peut nécessiter un remplissage interne implicite selon le membre précédent.

- Taille de la structure doit être un multiple entier de son alignement, laquelle peut requérir une marge intérieure après le dernier membre. Dans la mesure où les structures et les unions peuvent être regroupées dans des tableaux, chaque élément du tableau d’une structure ou une union doit commencer et se terminer à l’alignement correct préalablement déterminée.

- Il est possible d’aligner les données de manière à être supérieure à la configuration requise d’alignement, que les règles précédentes sont conservées.

- Un compilateur individuel peut ajuster la compression d’une structure pour des raisons de taille. Par exemple [/Zp (alignement des membres de Struct)](../build/reference/zp-struct-member-alignment.md) permet d’ajuster l’emballage de structures.

## <a name="see-also"></a>Voir aussi

[Types et stockage](../build/types-and-storage.md)
