---
title: Avertissement du compilateur (niveau 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 664b1b3ec732c323d0074310902890cdd6eca9a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588592"
---
# <a name="compiler-warning-level-2-c4653"></a>Avertissement du compilateur (niveau 2) C4653

option du compilateur 'option' non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours ignorée

Une option spécifiée avec l’utiliser des en-têtes précompilés ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) option était incompatible avec les options spécifiées lors de la création de l’en-tête précompilé. Cette compilation a utilisé l’option spécifiée lors de la création de l’en-tête précompilé.

Cet avertissement peut se produire lorsqu’une valeur différente de l’option Pack Structures ([/Zp](../../build/reference/zp-struct-member-alignment.md)) a été spécifiée pendant la compilation de l’en-tête précompilé.