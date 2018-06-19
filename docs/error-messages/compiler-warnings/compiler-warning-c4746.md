---
title: C4746 d’avertissement du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d00c75b2b7cdf2fdafb4e109496a701fb561cb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270896"
---
# <a name="compiler-warning-c4746"></a>C4746 d’avertissement du compilateur
accès volatile de '\<expression > » dépend : [iso&#124;ms] configuration ; envisagez d’utiliser des fonctions intrinsèques __iso_volatile_load/store.  
  
 C4746 est émis chaque fois qu’une variable volatile est accessible directement. Il vise à aider les développeurs à identifier les emplacements de code qui sont affectées par le modèle volatil spécifique actuellement spécifié (qui peuvent être contrôlé par le [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur). En particulier, il peut être utile pour la localisation des barrières de mémoire généré par le compilateur de matériel lorsque /volatile:ms est utilisé.  
  
 Les fonctions intrinsèques __iso_volatile_load/store peuvent être utilisés pour accéder explicitement les mémoire volatile sans être affecté par le modèle volatil. À l’aide de ces fonctions intrinsèques ne déclenche pas C4746.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.