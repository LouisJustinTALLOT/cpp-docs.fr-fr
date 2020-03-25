---
title: Avertissement du compilateur (niveau 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161735"
---
# <a name="compiler-warning-level-2-c4653"></a>Avertissement du compilateur (niveau 2) C4653

option du compilateur’option’non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours ignorée

Une option spécifiée avec l’option utiliser des en-têtes précompilés ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) n’était pas cohérente avec les options spécifiées lors de la création de l’en-tête précompilé. Cette compilation utilisait l’option spécifiée lors de la création de l’en-tête précompilé.

Cet avertissement peut se produire lorsqu’une valeur différente pour l’option Pack structures ([/ZP](../../build/reference/zp-struct-member-alignment.md)) a été spécifiée lors de la compilation de l’en-tête précompilé.
