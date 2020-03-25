---
title: Erreur irrécupérable NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193392"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099

dépassement de capacité de la pile

Le Makefile en cours de traitement était trop complexe pour l’allocation de pile actuelle dans NMAKE. NMAKE a une allocation de 0x3000 (12K).

Pour augmenter l’allocation de pile de NMAKE, exécutez l’utilitaire [EDITBIN/Stack](../../build/reference/stack.md) avec une option de pile plus grande :

**EDITBIN/STACK : réserver NMAKE. EXÉCUTABLE**

où *Reserve* est un nombre supérieur à l’allocation de pile actuelle dans NMAKE.
