---
title: Erreur irrécupérable NMAKE U1099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ef75a1435d8c922087fcdd21d1941961bc82cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113381"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099

dépassement de capacité de la pile

Le makefile en cours de traitement était trop complexe pour la taille de la pile dans NMAKE. NMAKE a une allocation de 0 x 3000 (12 Ko).

Pour augmenter l’allocation de piles de NMAKE, exécutez le [editbin /stack](../../build/reference/stack.md) utilitaire avec une option de pile plus importante :

**EDITBIN /STACK:reserve NMAKE. EXE**

où *réserver* est un nombre supérieur à l’allocation de pile en cours dans NMAKE.