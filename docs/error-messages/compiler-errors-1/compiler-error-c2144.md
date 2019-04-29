---
title: Erreur du compilateur C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: a75330d26b0924e60f7e46d10d617341709d7e23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353493"
---
# <a name="compiler-error-c2144"></a>Erreur du compilateur C2144

> Erreur de syntaxe : '*type*'doit être précédé par'*jeton*'

Le compilateur attendu *jeton* et trouvé *type* à la place.

Cette erreur peut résulter d’une accolade fermante manquante, une parenthèse droite ou un point-virgule.

C2144 peut également se produire lorsque vous tentez de créer une macro à partir d’un mot clé CLR qui contient un caractère espace blanc.

Vous pouvez également voir C2144 si vous essayez d’effectuer le transfert de type. Consultez [transfert de Type (C++ / c++ / CLI)](../../extensions/type-forwarding-cpp-cli.md) pour plus d’informations.

## <a name="examples"></a>Exemples

L’exemple suivant génère C2144 et illustre une méthode permettant de résoudre le problème :

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

L’exemple suivant génère C2144 et illustre une méthode permettant de résoudre le problème :

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```