---
description: 'En savoir plus sur : erreur du compilateur C2244'
title: Erreur du compilateur C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 9f541eca155b9d728f0bbf7cb1578a6e3424c49c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302238"
---
# <a name="compiler-error-c2244"></a>Erreur du compilateur C2244

'identificateur' : impossible de faire correspondre la définition de fonction à une déclaration existante

Une utilisation inhabituelle de l’opérateur unaire + a été utilisée devant un appel de fonction qui n’avait pas de parenthèses.

Cette erreur se produit uniquement dans les projets C++.

L’exemple suivant génère l’C2244 :

```cpp
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

C2244 peut également se produire lorsqu’une signature de fonction incorrecte est utilisée pour une fonction membre d’un modèle de classe.

```cpp
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

C2244 peut également se produire lorsqu’une signature de fonction incorrecte est utilisée pour un modèle de fonction membre.

```cpp
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

Vous ne pouvez pas spécialiser partiellement un modèle de fonction.

```cpp
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```
