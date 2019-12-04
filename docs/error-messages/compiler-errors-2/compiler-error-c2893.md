---
title: Erreur du compilateur C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760874"
---
# <a name="compiler-error-c2893"></a>Erreur du compilateur C2893

Échec de la spécialisation du modèle de fonction’template Name'

Le compilateur n’a pas pu spécialiser un modèle de fonction. Cette erreur peut avoir plusieurs causes.

En général, la façon de résoudre une erreur C2893 consiste à examiner la signature de la fonction et à vérifier que vous pouvez instancier chaque type.

## <a name="example"></a>Exemple

C2893 se produit parce que le paramètre de modèle de `f``T` est déduit pour être `std::map<int,int>`, mais `std::map<int,int>` n’a pas de `data_type` de membre (`T::data_type` ne peut pas être instancié avec `T = std::map<int,int>`.). L’exemple suivant génère l’C2893.

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
