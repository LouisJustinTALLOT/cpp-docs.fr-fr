---
title: Compilateur avertissement (niveau 1) C4717 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4717
dev_langs:
- C++
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa953d8d41003ff53e721671845c1ddee26da640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282426"
---
# <a name="compiler-warning-level-1-c4717"></a>Avertissement du compilateur (niveau 1) C4717
'fonction' : récurrent sur tous les chemins d’accès de contrôle, la fonction entraînera un débordement de pile d’exécution  
  
 Chaque chemin d’accès via une fonction contienne un appel à la fonction. Dans la mesure où il n’existe aucun moyen pour quitter la fonction sans appeler d’abord lui-même de manière récursive, la fonction ne se ferme jamais.  
  
 L’exemple suivant génère C4717 :  
  
```  
// C4717.cpp  
// compile with: /W1 /c  
// C4717 expected  
int func(int x) {  
   if (x > 1)  
      return func(x - 1); // recursive call  
   else {  
      int y = func(0) + 1; // recursive call  
      return y;  
   }  
}  
  
int main(){  
   func(1);  
}  
```