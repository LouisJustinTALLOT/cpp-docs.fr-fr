---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2020'
title: Erreur des outils Éditeur de liens LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 61e999b2f451359e3a806bc2da5f2beb431e6fab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275852"
---
# <a name="linker-tools-error-lnk2020"></a>Erreur des outils Éditeur de liens LNK2020

jeton’Token’non résolu

Semblable à une erreur externe non définie, à ceci près que la référence est via des métadonnées. Dans les métadonnées, toutes les fonctions et les données doivent être définies.

Pour résoudre ce problème :

- Définir la fonction ou les données manquantes, ou

- Incluez le fichier objet ou la bibliothèque dans lequel la fonction ou les données manquantes sont déjà définies.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’LNK2020.

```cpp
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

LNK2020 se produira également si vous créez une variable d’un type de modèle managé, mais que vous n’instanciez pas également le type.

L’exemple suivant génère l’LNK2020.

```cpp
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
