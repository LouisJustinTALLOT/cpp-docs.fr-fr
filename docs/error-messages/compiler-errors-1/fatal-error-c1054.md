---
title: Erreur irrécupérable C1054 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9daac4944c57dbf08fe0ebcbc95993a97838585
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198896"
---
# <a name="fatal-error-c1054"></a>Erreur irrécupérable C1054
limite du compilateur : initialiseurs imbriqués trop profondément  
  
 Le code dépasse la limite d’imbrication des initialiseurs (10-15 niveaux, selon la combinaison de types initialisés).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Simplifiez les types de données en cours d’initialisation pour réduire l’imbrication.  
  
2.  Initialiser les variables dans des instructions distinctes après la déclaration.