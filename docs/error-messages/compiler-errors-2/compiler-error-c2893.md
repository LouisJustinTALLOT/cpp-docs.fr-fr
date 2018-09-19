---
title: Erreur du compilateur C2893 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73d4f838f030db3667b08295006c2ea1df94c87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026177"
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