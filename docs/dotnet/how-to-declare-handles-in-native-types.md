---
title: 'Comment : déclarer des Handles dans les Types natifs | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fbf2934c2d7a1192e55ee9b454f91e7e8cc7037f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431266"
---
# <a name="how-to-declare-handles-in-native-types"></a>Comment : déclarer des handles dans les types natifs

Vous ne pouvez pas déclarer un type de handle dans un type natif. vcclr.h fournit le modèle de wrapper de type sécurisé `gcroot` pour faire référence à un objet CLR à partir du tas C++. Ce modèle vous permet d’incorporer un handle virtuel dans un type natif et le traitent comme s’il s’agissait du type sous-jacent. Dans la plupart des cas, vous pouvez utiliser le `gcroot` objet en tant que type incorporé sans transtypage. Toutefois, avec [pour chacun, dans](../dotnet/for-each-in.md), vous devez utiliser `static_cast` pour récupérer la référence managée sous-jacente.

Le `gcroot` modèle est implémenté à l’aide des fonctionnalités de la classe de valeur System::Runtime::InteropServices::GCHandle, qui fournit des « handles » dans le tas de garbage collection. Notez que les handles eux-mêmes ne sont pas nettoyées et sont libérées lorsqu’elles ne sont plus en cours d’utilisation par le destructeur dans la `gcroot` classe (ce destructeur ne peut pas être appelé manuellement). Si vous instanciez un `gcroot` de l’objet sur le tas natif, vous devez appeler delete sur cette ressource.

Le runtime gère une association entre le handle et l’objet CLR, qui elle fait référence. Lorsque l’objet CLR se déplace avec le tas de garbage collector, le handle retourne la nouvelle adresse de l’objet. Une variable ne devra pas être épinglé avant lui est attribuée à un `gcroot` modèle.

## <a name="example"></a>Exemple

Cet exemple montre comment créer un `gcroot` objet sur la pile native.

```
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

Cet exemple montre comment créer un `gcroot` objet sur le tas natif.

```
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

Cet exemple montre comment utiliser `gcroot` pour contenir des références à des types valeur (pas les types référence) dans un type natif à l’aide de `gcroot` sur le type boxed.

```
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