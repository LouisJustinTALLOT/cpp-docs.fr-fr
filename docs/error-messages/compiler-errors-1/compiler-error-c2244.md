---
title: Erreur du compilateur C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 7cfa0cd7ff4290ca5f07fb712bbcac7dabf55f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301394"
---
# <a name="compiler-error-c2244"></a>Erreur du compilateur C2244

'identificateur' : Impossible de faire correspondre la définition de fonction avec une déclaration existante

Une utilisation inhabituelle de l’opérateur unaire + a été utilisée devant un appel de fonction qui n’avait pas de parenthèse.

Cette erreur se produit uniquement dans les projets C++.

L’exemple suivant génère l’erreur C2244 :

```
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

L’erreur C2244 peut également se produire lorsqu’une signature de fonction incorrecte est utilisée pour une fonction membre d’un modèle de classe.

```
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

L’erreur C2244 peut également se produire lorsqu’une signature de fonction incorrecte est utilisée pour un modèle de fonction membre.

```
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

```
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```