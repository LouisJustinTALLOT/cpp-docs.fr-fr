---
title: Balise de direction
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: ae2936c4e07a434a49d931ed60a7d7dee74e3177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534876"
---
# <a name="direction-flag"></a>Balise de direction

L’indicateur de direction est un indicateur de processeur spécifique pour les processeurs Intel 80x86. Il s’applique à toutes les instructions d’assembly qui utilisent le préfixe REP (répétition) REP, comme AVI, MOVSD, MOVSW et d’autres. Les adresses fournies aux instructions applicables sont augmentées si l’indicateur de direction est désactivé.

Les routines d’exécution C partent du principe que l’indicateur de direction est désactivé. Si vous utilisez d’autres fonctions avec les fonctions runtime C, vous devez vous assurer que les autres fonctions ne touchent pas à l’indicateur de direction ou qu’elles le restaurent à son état d’origine. Supposer que l’indicateur de direction est désactivé lors de l’entrée rend le code d’exécution plus rapide et plus efficace.

Les fonctions de bibliothèque Runtime C, comme les routines de manipulation de chaînes et de manipulation de la mémoire tampon s’attendent à ce que l’indicateur de direction soit désactivé.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)