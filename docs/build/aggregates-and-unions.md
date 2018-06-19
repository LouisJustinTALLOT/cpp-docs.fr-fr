---
title: Agrégats et Unions | Documents Microsoft
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
ms.openlocfilehash: 5b1afd3be89e1d18da9889d88dbbbef3fb104e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363257"
---
# <a name="aggregates-and-unions"></a>Agrégats et unions
D’autres types, tels que des tableaux, structures et unions, ont des exigences plus strictes alignement qui garantissent la cohérence union et d’agrégation stockage et extraction des données. Voici les définitions de tableau, la structure et union :  
  
 Tableau  
 Contient un groupe ordonné d’objets de données adjacents. Chaque objet est appelé un élément. Tous les éléments dans un tableau ont la même taille et type de données.  
  
 Structure  
 Contient un groupe ordonné d’objets de données. Contrairement aux éléments d’un tableau, les objets de données dans une structure peuvent avoir des tailles et des types de données différents. Chaque objet de données dans une structure est appelé membre.  
  
 Union  
 Objet qui contient l’un d’un jeu de membres nommés. Les membres du jeu nommé peuvent être de n’importe quel type. Le stockage alloué pour une union est égal au stockage requis pour le plus grand membre de cette union, plus tout remplissage requis pour l’alignement.  
  
 Le tableau suivant présente l’alignement vivement recommandé pour les membres scalaires de structures et unions.  
  
||||  
|-|-|-|  
|Type scalaire|Type de données C|Alignement requis|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Word|  
|**UINT16**|**unsigned short**|Word|  
|**INT32**|**int, long**|Mot double|  
|**UINT32**|**entier long non signé**|Mot double|  
|**INT64**|`__int64`|Mot quadruple|  
|**UINT64**|**unsigned __int64**|Mot quadruple|  
|**FP32 (simple précision)**|**float**|Mot double|  
|**FP64 (double précision)**|**double**|Mot quadruple|  
|**POINTEUR**|**\***|Mot quadruple|  
|`__m64`|**__m64 struct**|Mot quadruple|  
|`__m128`|**struct __m128**|Octaword|  
  
 Les règles d’alignement d’agrégation suivantes s’appliquent :  
  
-   L’alignement d’un tableau est le même que l’alignement de l’un des éléments du tableau.  
  
-   L’alignement du début d’une structure ou une union est l’alignement maximal de tout membre individuel. Chaque membre au sein de la structure ou union doit être placé à son propre alignement comme défini dans le tableau précédent, ce qui peut nécessiter un remplissage interne implicite selon le membre précédent.  
  
-   Taille de la structure doit être un multiple intégral de son alignement, qui peut exiger un remplissage après le dernier membre. Étant donné que les structures et les unions peuvent être regroupées dans des tableaux, chaque élément du tableau d’une structure ou une union doit commencer et se terminer à l’alignement correct déterminé précédemment.  
  
-   Il est possible d’aligner les données de manière à être supérieure à la configuration requise d’alignement tant que les règles précédentes sont conservées.  
  
-   Un compilateur individuel peut ajuster la compression d’une structure pour des raisons de taille. Par exemple [/Zp (alignement des membres de Struct)](../build/reference/zp-struct-member-alignment.md) permet d’ajuster la compression des structures.  
  
## <a name="see-also"></a>Voir aussi  
 [Types et stockage](../build/types-and-storage.md)
