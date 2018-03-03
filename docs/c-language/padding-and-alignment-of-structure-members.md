---
title: Stockage et alignement de membres de structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cd8dc389f4a4140b78a78753f7f5a91168bd984
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="padding-and-alignment-of-structure-members"></a>Remplissage et alignement des membres de structure
**ANSI 3.5.2.1** Indique le remplissage et l'alignement des membres de structures et détermine si un champ de bits peut chevaucher une limite d'unité de stockage  
  
 Les membres d'une structure sont stockés de manière séquentielle dans l'ordre dans lequel ils sont déclarés : le premier membre a l'adresse mémoire la plus basse et le dernier la plus élevée.  
  
 Chaque objet de données possède une spécification d'alignement. La spécification d'alignement pour toutes les données à l'exception des structures, des unions et les tableaux est la taille de l'objet ou la taille de compression actuelle (spécifiée avec /Zp ou le pragma `pack`, selon la valeur la plus petite). Pour les structures, les unions et les tableaux, la spécification d'alignement correspond à la plus grande spécification d'alignement de ses membres. Un décalage est alloué à chaque objet afin que  
  
 *offset*  `%` *alignment-requirement* `==` 0  
  
 Les champs de bits adjacents sont empaquetés dans la même unité d’allocation de 1, 2 ou 4 octets si les types intégraux sont de la même taille et si le champ de bits suivant s’insère dans l’unité d’allocation actuelle sans dépasser la limite imposée par les exigences d’alignement courantes des champs de bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, unions, énumérations et champs de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)