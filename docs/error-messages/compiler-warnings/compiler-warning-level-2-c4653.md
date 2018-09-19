---
title: Compilateur avertissement (niveau 2) C4653 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4653
dev_langs:
- C++
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 376da24d4619eacc3e6b3defe8fdfc582800a898
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045976"
---
# <a name="compiler-warning-level-2-c4653"></a>Avertissement du compilateur (niveau 2) C4653

option du compilateur 'option' non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours ignorée

Une option spécifiée avec l’utiliser des en-têtes précompilés ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) option était incompatible avec les options spécifiées lors de la création de l’en-tête précompilé. Cette compilation a utilisé l’option spécifiée lors de la création de l’en-tête précompilé.

Cet avertissement peut se produire lorsqu’une valeur différente de l’option Pack Structures ([/Zp](../../build/reference/zp-struct-member-alignment.md)) a été spécifiée pendant la compilation de l’en-tête précompilé.