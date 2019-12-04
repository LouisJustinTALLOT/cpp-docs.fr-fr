---
title: Erreur du compilateur C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 76fd2363b6139bc1bc04aa4d4949a12522e31aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751792"
---
# <a name="compiler-error-c2976"></a>Erreur du compilateur C2976

'identificateur' : arguments de type insuffisants

Un ou plusieurs arguments réels sont manquants dans un générique ou un modèle. Vérifiez la déclaration du générique ou du modèle pour connaître le nombre de paramètres approprié.

Cette erreur peut être due à l’absence d’arguments C++ template dans les composants de la bibliothèque standard.

L’exemple suivant génère l’C2976 :

```cpp
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

C2976 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```
