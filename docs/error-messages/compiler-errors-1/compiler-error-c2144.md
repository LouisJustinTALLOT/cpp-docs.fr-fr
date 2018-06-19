---
title: Erreur du compilateur C2144 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2144
dev_langs:
- C++
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60a6b0a6019ab6ddf1a403d2cbd4f6ef96b2a865
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171145"
---
# <a name="compiler-error-c2144"></a>Erreur du compilateur C2144

> Erreur de syntaxe : '*type*'doit être précédée par'*jeton*'

Le compilateur attendu *jeton* et *type* à la place.

Cette erreur peut résulter d’une accolade fermante manquante, une parenthèse fermante ou un point-virgule.

C2144 peut également se produire lorsque vous tentez de créer une macro à partir d’un mot clé CLR qui contient un caractère espace blanc.

Vous pouvez également voir C2144 si vous tentez d’effectuer une transmission de type. Consultez [transfert de Type (C + c++ / CLI)](../../windows/type-forwarding-cpp-cli.md) pour plus d’informations.

## <a name="examples"></a>Exemples

L’exemple suivant génère le C2144 et illustre une méthode pour résoudre ce problème :

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

L’exemple suivant génère le C2144 et illustre une méthode pour résoudre ce problème :

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