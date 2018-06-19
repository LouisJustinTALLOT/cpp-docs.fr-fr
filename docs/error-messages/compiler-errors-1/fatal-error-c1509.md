---
title: Erreur irrécupérable C1509 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198792"
---
# <a name="fatal-error-c1509"></a>Erreur irrécupérable C1509
limite du compilateur : trop d’états de gestionnaire d’exception dans la fonction 'fonction'. Simplifiez la fonction.  
  
 Le code dépasse une limite interne sur les États de gestionnaire d’exceptions (32 768 états).  
  
 La cause la plus courante est que la fonction contient une expression complexe de variables de la classe définie par l’utilisateur et d’opérateurs arithmétiques.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Simplifiez les expressions en assignant des sous-expressions communes à des variables temporaires.  
  
2.  Fractionnez la fonction en fonctions plus petites.