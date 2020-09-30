---
title: Balise de direction
description: Décrit l’effet de l’indicateur de direction de l’UC sur les fonctions Microsoft C Runtime.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: a8f06b3b8caf08e1d3db2159bfc730e25229733b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589989"
---
# <a name="direction-flag"></a>Balise de direction

L’indicateur de direction est un indicateur de processeur spécifique à tous les processeurs compatibles avec Intel x86. Il s’applique à toutes les instructions d’assembly qui utilisent le préfixe REP (répétition) REP, comme AVI, MOVSD, MOVSW et d’autres. Les adresses fournies aux instructions applicables sont augmentées si l’indicateur de direction est désactivé.

Les routines d’exécution C partent du principe que l’indicateur de direction est désactivé. Si vous utilisez d’autres fonctions avec les fonctions runtime C, vous devez vous assurer que les autres fonctions ne touchent pas à l’indicateur de direction ou qu’elles le restaurent à son état d’origine. Supposer que l’indicateur de direction est désactivé lors de l’entrée rend le code d’exécution plus rapide et plus efficace.

Les fonctions de bibliothèque Runtime C, comme les routines de manipulation de chaînes et de manipulation de la mémoire tampon s’attendent à ce que l’indicateur de direction soit désactivé.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
