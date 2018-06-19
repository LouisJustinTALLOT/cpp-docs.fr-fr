---
title: Erreur irrécupérable C1002 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225049"
---
# <a name="fatal-error-c1002"></a>Erreur irrécupérable C1002
espace du tas insuffisant pour le compilateur lors de la deuxième passe  
  
 Le compilateur a manqué d’espace mémoire dynamique, la deuxième phase, probablement en raison d’un programme avec trop de symboles ou d’expressions complexes.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Fractionnez le fichier source en plusieurs fichiers plus petits.  
  
2.  Fractionnez les expressions en sous-expressions plus petites.  
  
3.  Supprimer d’autres programmes ou les pilotes qui consomment de la mémoire.