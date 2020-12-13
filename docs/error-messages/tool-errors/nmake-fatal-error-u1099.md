---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1099'
title: Erreur irrécupérable NMAKE U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 8044010cf967e4fe27b2235968022023d66ae1c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345314"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099

dépassement de capacité de la pile

Le Makefile en cours de traitement était trop complexe pour l’allocation de pile actuelle dans NMAKE. NMAKE a une allocation de 0x3000 (12K).

Pour augmenter l’allocation de pile de NMAKE, exécutez l’utilitaire [EDITBIN/Stack](../../build/reference/stack.md) avec une option de pile plus grande :

**EDITBIN/STACK : Reserve NMAKE.EXE**

où *Reserve* est un nombre supérieur à l’allocation de pile actuelle dans NMAKE.
