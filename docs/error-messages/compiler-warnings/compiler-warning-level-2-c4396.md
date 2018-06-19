---
title: Compilateur avertissement (niveau 2) C4396 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b937b6ecebedc6984279502a5f64b287f09bd2d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290668"
---
# <a name="compiler-warning-level-2-c4396"></a>Avertissement du compilateur (niveau 2) C4396
'nom' : le spécificateur inline ne peut pas être utilisé lorsqu’une déclaration friend se réfère à une spécialisation d’un modèle de fonction  
  
 Une spécialisation d’un modèle de fonction ne peut pas spécifier n’importe quel de la [inline](../../cpp/inline-functions-cpp.md) spécificateurs. Le compilateur émet l’avertissement C4396 et ignore le spécificateur inline.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez le spécificateur `inline`, `__inline`ou `__forceinline` de la déclaration de la fonction friend.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre une déclaration de fonction friend non valide avec un spécificateur `inline` .  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```