---
title: 'Comment : déclarer des handles dans les types natifs'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988246"
---
# <a name="how-to-declare-handles-in-native-types"></a>Comment : déclarer des handles dans les types natifs

Vous ne pouvez pas déclarer un type de handle dans un type natif. Vcclr. h fournit le modèle de wrapper de type sécurisé `gcroot` pour faire référence à un objet CLR C++ à partir du tas. Ce modèle vous permet d’incorporer un handle virtuel dans un type natif et de le traiter comme s’il s’agissait du type sous-jacent. Dans la plupart des cas, vous pouvez utiliser l’objet `gcroot` comme type incorporé sans cast. Toutefois, avec [pour chaque, dans](../dotnet/for-each-in.md), vous devez utiliser `static_cast` pour récupérer la référence managée sous-jacente.

Le modèle `gcroot` est implémenté à l’aide des fonctionnalités de la classe value System :: Runtime :: InteropServices :: GCHandle, qui fournit des « handles » dans le tas récupéré par le garbage collector. Notez que les handles eux-mêmes ne sont pas récupérés par le garbage collector et sont libérés lorsqu’ils ne sont plus utilisés par le destructeur de la classe `gcroot` (ce destructeur ne peut pas être appelé manuellement). Si vous instanciez un objet `gcroot` sur le tas natif, vous devez appeler Delete sur cette ressource.

Le runtime maintiendra une association entre le handle et l’objet CLR, qu’il référence. Lorsque l’objet CLR est déplacé avec le tas récupéré par le garbage collector, le handle retourne la nouvelle adresse de l’objet. Une variable ne doit pas être épinglée avant d’être assignée à un modèle de `gcroot`.

## <a name="example"></a>Exemple

Cet exemple montre comment créer un objet `gcroot` sur la pile native.

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>Exemple

Cet exemple montre comment créer un objet `gcroot` sur le tas natif.

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>Exemple

Cet exemple montre comment utiliser `gcroot` pour stocker des références à des types valeur (et non des types référence) dans un type natif à l’aide de `gcroot` sur le type boxed.

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
