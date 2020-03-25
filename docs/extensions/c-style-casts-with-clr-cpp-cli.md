---
title: Casts de style C avec /clr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: 2b7e492c62047e3b38224637f842d8a7fcbae84f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172592"
---
# <a name="c-style-casts-with-clr-ccli"></a>Casts de style C avec /clr (C++/CLI)

La rubrique suivante s’applique uniquement au Common Language Runtime.

Lorsqu’il est utilisé avec les types CLR, le compilateur tente de mapper le cast de type C sur l’un des casts répertoriés ci-dessous, dans l’ordre suivant :

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

Si aucun des casts répertoriés ci-dessus n’est valide, et si le type de l’expression et le type de cible sont des types de référence CLR, le cast de style C est mappé à une vérification du runtime (instruction MSIL castclass). Sinon, un cast de style C est considéré comme non valide et le compilateur génère une erreur.

## <a name="remarks"></a>Notes

Un cast de style C n’est pas recommandé. Lors de la compilation avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), utilisez [safe_cast](safe-cast-cpp-component-extensions.md).

L’exemple suivant montre un cast de style C qui est mappé à un **const_cast**.

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

L’exemple suivant montre un cast de style C qui est mappé à un **safe_cast**.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

L’exemple suivant montre un cast de style C qui est mappé à un **safe_cast** et un **const_cast**.

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

L’exemple suivant montre un cast de style C qui est mappé à un **static_cast**.

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

L’exemple suivant montre un cast de style C qui est mappé à un **static_cast** et un **const_cast**.

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

L’exemple suivant montre un cast de style C qui est mappé à un contrôle de l’exécution.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

L’exemple suivant montre un cast de style C non valide, lequel provoque la génération d’une erreur par le compilateur.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
