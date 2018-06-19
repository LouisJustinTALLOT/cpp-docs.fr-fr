---
title: Erreur du compilateur C2753 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2753
dev_langs:
- C++
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acbf5736c7c263293bc1c2782cab7df4f0af2083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235361"
---
# <a name="compiler-error-c2753"></a>Erreur du compilateur C2753
'*modèle*' : une spécialisation partielle ne peuvent pas correspondre la liste d’arguments pour le modèle principal  
  
 Si la liste d’arguments template correspond à la liste de paramètres, le compilateur le traite comme le même modèle. Définition de deux fois le même modèle n’est pas autorisée.  
  
## <a name="example"></a>Exemple
 L’exemple suivant génère l’erreur C2753 et illustre une méthode pour résoudre ce problème :  
  
```cpp  
// C2753.cpp  
// compile with: cl /c C2753.cpp
template<class T>  
struct A {};  
  
template<class T>  
struct A<T> {};   // C2753  
// try the following line instead  
// struct A<int> {};  
  
template<class T, class U, class V, class W, class X>  
struct B {};  
```