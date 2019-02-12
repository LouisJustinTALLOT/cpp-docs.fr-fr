---
title: Indicateur de direction
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: e5177f206e46227fa693ef8d4bd1848b06374af7
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849904"
---
# <a name="direction-flag"></a>Indicateur de direction

L’indicateur de direction est un indicateur de processeur spécifique à tous les processeurs compatibles avec Intel x86. Il s’applique à toutes les instructions d’assembly qui utilisent le préfixe REP (répétition) REP, comme AVI, MOVSD, MOVSW et d’autres. Les adresses fournies aux instructions applicables sont augmentées si l’indicateur de direction est désactivé.

Les routines d’exécution C partent du principe que l’indicateur de direction est désactivé. Si vous utilisez d’autres fonctions avec les fonctions runtime C, vous devez vous assurer que les autres fonctions ne touchent pas à l’indicateur de direction ou qu’elles le restaurent à son état d’origine. Supposer que l’indicateur de direction est désactivé lors de l’entrée rend le code d’exécution plus rapide et plus efficace.

Les fonctions de bibliothèque Runtime C, comme les routines de manipulation de chaînes et de manipulation de la mémoire tampon s’attendent à ce que l’indicateur de direction soit désactivé.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)
