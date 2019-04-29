---
title: Erreur des outils Éditeur de liens LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386328"
---
# <a name="linker-tools-error-lnk2020"></a>Erreur des outils Éditeur de liens LNK2020

jeton non résolu 'token'

Semblable à une erreur externe non définie, sauf que la référence est par le biais de métadonnées. Dans les métadonnées, toutes les fonctions et des données doivent être définies.

Pour résoudre :

- Définir la fonction manquante ou des données, ou

- Inclure le fichier objet ou la bibliothèque dans lequel la fonction ou les données manquantes sont déjà définies.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK2020.

```
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>Exemple

LNK2020 se produira également si vous créez une variable d’un type de modèle managé, mais que vous n’instanciez pas également le type.

L’exemple suivant génère l’erreur LNK2020.

```
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```