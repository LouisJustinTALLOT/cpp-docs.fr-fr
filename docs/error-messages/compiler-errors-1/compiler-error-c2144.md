---
description: 'En savoir plus sur : erreur du compilateur C2144'
title: Erreur du compilateur C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: 172ccb897937008aa305616eea19f234dfc6a3bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235500"
---
# <a name="compiler-error-c2144"></a>Erreur du compilateur C2144

> erreur de syntaxe : '*type*'doit être précédé de'*Token*'

Le compilateur attendait un *jeton* et un *type* trouvé à la place.

Cette erreur peut être due à l’absence d’une accolade fermante, d’une parenthèse droite ou d’un point-virgule.

C2144 peut également se produire lors d’une tentative de création d’une macro à partir d’un mot clé CLR qui contient un espace blanc.

Vous pouvez également voir C2144 si vous essayez d’effectuer le transfert de type. Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2144 et montre un moyen de le corriger :

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

L’exemple suivant génère l’C2144 et montre un moyen de le corriger :

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
