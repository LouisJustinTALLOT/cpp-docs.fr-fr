---
title: Avertissement du compilateur (niveau 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199566"
---
# <a name="compiler-warning-level-1-c4650"></a>Avertissement du compilateur (niveau 1) C4650

informations de débogage absentes de l’en-tête précompilé ; Seuls les symboles globaux de l’en-tête seront disponibles

Le fichier d’en-tête précompilé n’a pas été compilé avec les informations de débogage symboliques de Microsoft.

Lorsqu’il est lié, le fichier exécutable ou de bibliothèque de liens dynamiques qui en résulte n’inclut pas les informations de débogage pour les symboles locaux contenus dans l’en-tête précompilé.

Cet avertissement peut être évité en recompilant le fichier d’en-tête précompilé avec l’option de ligne de commande [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .
