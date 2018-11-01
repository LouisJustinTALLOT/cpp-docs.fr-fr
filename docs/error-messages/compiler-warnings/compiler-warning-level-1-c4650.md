---
title: Avertissement du compilateur (niveau 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536098"
---
# <a name="compiler-warning-level-1-c4650"></a>Avertissement du compilateur (niveau 1) C4650

informations de débogage pas dans l’en-tête précompilé ; Seuls les symboles globaux de l’en-tête seront disponibles

Le fichier d’en-tête précompilé n’a pas été compilé avec les informations de débogage symboliques à Microsoft.

Lorsque lié, le fichier exécutable ou DLL de bibliothèque n’inclura pas les informations de débogage pour les symboles locaux contenus dans l’en-tête précompilé.

Cet avertissement peut être évité en recompilant le fichier d’en-tête précompilé avec le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option de ligne de commande.