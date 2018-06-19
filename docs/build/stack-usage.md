---
title: L’utilisation de la pile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f711636089a6f2966002002220aac88cebe17a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379856"
---
# <a name="stack-usage"></a>Utilisation de la pile
Toute la mémoire au-delà de l’adresse actuelle de RSP est considérée comme volatile : le système d’exploitation ou un débogueur, peut remplacer cette mémoire pendant une session de débogage d’utilisateur ou un gestionnaire d’interruption. Par conséquent, RSP doit toujours être défini avant de tenter de lire ou écrire des valeurs dans un frame de pile.  
  
 Cette section décrit l’allocation d’espace de pile pour les variables locales et les **alloca** intrinsèque.  
  
-   [Allocation de piles](../build/stack-allocation.md)  
  
-   [Construction dynamique d’une zone pour la pile de paramètres](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Types de fonctions](../build/function-types.md)  
  
-   [Alignement avec malloc](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions des logiciels x64](../build/x64-software-conventions.md)