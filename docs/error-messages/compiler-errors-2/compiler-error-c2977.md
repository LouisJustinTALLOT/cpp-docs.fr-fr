---
description: 'En savoir plus sur : erreur du compilateur C2977'
title: Erreur du compilateur C2977
ms.date: 11/04/2016
f1_keywords:
- C2977
helpviewer_keywords:
- C2977
ms.assetid: 3c4218e0-5d03-4a2b-b757-c507c35f3542
ms.openlocfilehash: f58c3396bb2958623a4275ba9dc4d2787d0d3c06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281884"
---
# <a name="compiler-error-c2977"></a>Erreur du compilateur C2977

'identifier' : arguments de type trop nombreux

Un générique ou un modèle possède trop d’arguments réels. Vérifiez la déclaration du générique ou du modèle pour connaître le nombre de paramètres approprié.

L’exemple suivant génère l’erreur C2977 :

```cpp
// C2977.cpp
// compile with: /c
template<class T, int i>
class MyClass {};

template MyClass< int , 1, 1 >;   // C2977
template MyClass< int , 1 >;   // OK
```

L’erreur C2977 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2977b.cpp
// compile with: /clr
// C2977 expected
generic <class T, class U>
void f(){}

generic <class T>
ref struct GC1 {};

int main() {
   // Delete the following 2 lines to resolve.
   GC1<int, char> ^ pgc1;
   f<int,int,int>();

   // OK
   GC1<int> ^ pgc1;
   f<int, int>();
}
```
