---
description: 'En savoir plus sur : erreur du compilateur C2893'
title: Erreur du compilateur C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: 42e31327096a539feeb691c698b52f57ecb615a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278257"
---
# <a name="compiler-error-c2893"></a>Erreur du compilateur C2893

Échec de la spécialisation du modèle de fonction’template Name'

Le compilateur n’a pas pu spécialiser un modèle de fonction. Cette erreur peut avoir plusieurs causes.

En général, la façon de résoudre une erreur C2893 consiste à examiner la signature de la fonction et à vérifier que vous pouvez instancier chaque type.

## <a name="example"></a>Exemple

C2893 se produit parce que le `f` paramètre de modèle de `T` est déduit comme étant, mais n’a pas de `std::map<int,int>` `std::map<int,int>` membre `data_type` ( `T::data_type` ne peut pas être instancié avec `T = std::map<int,int>` ). L’exemple suivant génère l’C2893.

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
