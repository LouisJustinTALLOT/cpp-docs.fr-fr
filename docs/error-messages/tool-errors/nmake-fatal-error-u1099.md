---
title: Erreur irrécupérable NMAKE U1099 | Documents Microsoft
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
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322102"
---
# <a name="nmake-fatal-error-u1099"></a>Erreur irrécupérable NMAKE U1099
dépassement de capacité de la pile  
  
 Le makefile en cours de traitement était trop complexe pour la taille de la pile dans NMAKE. NMAKE a une allocation de 0 x 3000 (12 Ko).  
  
 Pour augmenter l’allocation de pile de NMAKE, exécutez le [editbin /stack](../../build/reference/stack.md) utilitaire avec une option de pile plus importante :  
  
 **EDITBIN /STACK:reserve NMAKE. EXE**  
  
 où *réserver* est un nombre supérieur à l’allocation de pile en cours dans NMAKE.