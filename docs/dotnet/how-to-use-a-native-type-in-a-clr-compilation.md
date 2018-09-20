---
title: 'Comment : utiliser un Type natif dans une Compilation - clr | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e56c3617b6b2a8168e35867c09858dffa84cea9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448062"
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