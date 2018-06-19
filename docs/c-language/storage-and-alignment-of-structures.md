---
title: Stockage et alignement de structures | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4a70ab5fbeb4a1672279e7e9b617e3b4de1c1b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388128"
---
# <a name="storage-and-alignment-of-structures"></a>Stockage et alignement de structures
**Section spécifique à Microsoft**  
  
 Les membres d'une structure sont stockés de manière séquentielle dans l'ordre dans lequel ils sont déclarés : le premier membre a l'adresse mémoire la plus basse et le dernier la plus élevée.  
  
 Chaque objet de données possède un *alignment-requirement*. Pour les structures, l’exigence est le membre le plus grand. Un *décalage* est alloué à chaque objet afin que  
  
 *offset* `%` *alignment-requirement* `==` 0  
  
 Les champs de bits adjacents sont empaquetés dans la même unité d’allocation de 1, 2 ou 4 octets si les types intégraux sont de la même taille et si le champ de bits suivant s’insère dans l’unité d’allocation actuelle sans dépasser la limite imposée par les exigences d’alignement courantes des champs de bits.  
  
 Pour économiser l'espace ou se conformer aux structures de données existantes, vous pouvez stocker des structures de manière plus ou moins compacte. L’option du compilateur [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] et le [#pragma pack](../preprocessor/pack.md) contrôlent la façon dont les données de la structure sont « assemblées » en mémoire. Quand vous utilisez l’option /Zp[*n*], où *n* est 1, 2, 4, 8 ou 16, chaque membre de la structure après le premier est enregistré aux limites des octets qui représente la spécification d’alignement du champ ou la taille d’assemblage (*n*), selon celui qui est le plus petit. Les limites d'octets exprimées comme une formule sont  
  
```  
min( n, sizeof( item ) )  
```  
  
 où *n* est la taille d’assemblage exprimée avec l’option /Zp[*n*] et *item* est le membre de la structure. La taille de compression par défaut est /Zp8.  
  
 Pour utiliser le pragma `pack` pour spécifier une compression autre que celle spécifiée sur la ligne de commande pour une structure particulière, indiquez le pragma `pack`, où la taille de compression est 1, 2, 4, 8 ou 16, avant la structure. Pour rétablir la compression donnée sur la ligne de commande, spécifiez le pragma `pack` sans argument.  
  
 Pour le compilateur Microsoft C, la taille par défaut des champs de bits est **long**. Les membres de la structure sont alignés sur la taille du type ou sur la taille de /Zp[*n*], selon celle qui est la plus petite. La taille par défaut est 4.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations de structure](../c-language/structure-declarations.md)