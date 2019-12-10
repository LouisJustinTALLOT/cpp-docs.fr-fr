---
title: 'Comment : utiliser un type natif dans une compilation-CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: b506c3d825c4c26236a4ac3fc9682067a011315a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988426"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Comment : utiliser un type natif dans une compilation /clr

Vous pouvez définir un type natif dans une compilation **/CLR** et toute utilisation de ce type natif à partir de l’assembly est valide. Toutefois, les types natifs ne peuvent pas être utilisés à partir de métadonnées référencées.

Chaque assembly doit contenir la définition de chaque type natif qu’il utilisera.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

Cet exemple crée un composant qui définit et utilise un type natif.

```cpp
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

Cet exemple définit un client qui utilise le composant. Notez qu’il s’agit d’une erreur d’accès au type natif, sauf s’il est défini dans le compiland.

```cpp
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
