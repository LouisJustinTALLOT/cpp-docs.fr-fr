---
title: Erreur du compilateur C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455183"
---
# <a name="compiler-error-c2893"></a>Erreur du compilateur C2893

Échec de la spécialisation du modèle de fonction 'nom de modèle'

Le compilateur a échoué spécialiser un modèle de fonction. Il peut y avoir plusieurs causes pour cette erreur.

En règle générale, la manière de résoudre une erreur C2893 consiste à examiner la signature de la fonction et vérifiez que vous pouvez instancier chaque type.

## <a name="example"></a>Exemple

Erreur C2893 se produit parce que `f`du paramètre de modèle `T` est déduit pour être `std::map<int,int>`, mais `std::map<int,int>` n’a aucun membre `data_type` (`T::data_type` ne peut pas être instancié avec `T = std::map<int,int>`.). L’exemple suivant génère l’erreur C2893.

```
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