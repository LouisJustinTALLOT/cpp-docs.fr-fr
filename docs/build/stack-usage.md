---
title: L’utilisation de la pile | Microsoft Docs
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
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721537"
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