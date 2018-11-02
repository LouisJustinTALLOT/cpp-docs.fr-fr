---
title: 'Comment : utiliser un Type natif dans une Compilation - clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 0079be21b474858684e1abaaeb363820764a701d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459950"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Comment : utiliser un type natif dans une compilation /clr

Vous pouvez définir un type natif dans une **/CLR** compilation et toute utilisation de ce type natif à partir de l’assembly n’est valide. Toutefois, les types natifs ne sera pas disponibles pour une utilisation à partir des métadonnées référencées.

Chaque assembly doit contenir la définition de chaque type natif, qu'il utilisera.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

Cet exemple crée un composant qui définit et utilise un type natif.

```
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>Exemple

Cet exemple définit un client qui utilise le composant. Notez qu’il est une erreur pour accéder au type natif, sauf si elle est définie dans le module.

```
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)