---
title: Compilateur avertissement (niveau 1) C4651 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0015102a44b71f342b125532d20849590157ee0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283365"
---
# <a name="compiler-warning-level-1-c4651"></a>Avertissement du compilateur (niveau 1) C4651
'définition' spécifiée pour l’en-tête précompilé mais non pour la compilation en cours  
  
 La définition a été spécifiée lors de l’en-tête précompilé a été généré, mais pas dans cette compilation.  
  
 La définition soit appliqué à l’intérieur de l’en-tête précompilé, mais pas dans le reste du code.  
  
 Si un en-tête précompilé a été généré avec/DSYMBOL, le compilateur génère cet avertissement si la compilation /Yu ne comprend pas /DSYMBOL.  Ajout de /DSYMBOL à la ligne de commande /Yu résout cet avertissement.