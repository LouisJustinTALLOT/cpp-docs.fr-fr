---
title: Erreur du compilateur C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 02771d7419c58ee4f0b6d7db46ba91fde253d9a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428494"
---
# <a name="compiler-error-c2976"></a>Erreur du compilateur C2976

'identificateur' : trop peu d’arguments de type

Un générique ou un modèle il manque un ou plusieurs arguments réels. Vérifiez la déclaration du générique ou du modèle pour connaître le nombre de paramètres approprié.

Cette erreur peut être due à l’absence d’arguments template dans les composants de la bibliothèque C++ Standard.

L’exemple suivant génère l’erreur C2976 :

```
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

```
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