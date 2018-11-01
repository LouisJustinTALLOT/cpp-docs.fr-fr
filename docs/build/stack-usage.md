---
title: Utilisation de la pile
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452219"
---
# <a name="stack-usage"></a>Utilisation de la pile

Toute la mémoire au-delà de l’adresse actuelle de RSP est considérée comme volatile : le système d’exploitation ou d’un débogueur, peut remplacer cette mémoire pendant une session de débogage d’utilisateur ou un gestionnaire d’interruption. Par conséquent, RSP doit toujours être défini avant de tenter de lire ou écrire des valeurs dans un frame de pile.

Cette section décrit l’allocation d’espace de pile pour les variables locales et le **alloca** intrinsèque.

- [Allocation de piles](../build/stack-allocation.md)

- [Construction dynamique d’une zone pour la pile de paramètres](../build/dynamic-parameter-stack-area-construction.md)

- [Types de fonctions](../build/function-types.md)

- [Alignement avec malloc](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)