---
title: 'Procédure : Stocker la référence d’objet en mémoire non managée'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 0d8dc341d1fe2c61eba098abec9258a2c6dade79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387290"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Procédure : Stocker la référence d’objet en mémoire non managée

Vous pouvez utiliser gcroot.h, qui encapsule <xref:System.Runtime.InteropServices.GCHandle>, pour conserver une référence d’objet CLR dans la mémoire non managée. Vous pouvez également utiliser `GCHandle` directement.

## <a name="example"></a>Exemple

```
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

## <a name="example"></a>Exemple

`GCHandle` vous offre un moyen de stocker une référence d’objet managé dans la mémoire non managée.  Vous utilisez le <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> méthode pour créer un handle opaque vers un objet managé et <xref:System.Runtime.InteropServices.GCHandle.Free%2A> à le libérer. En outre, le <xref:System.Runtime.InteropServices.GCHandle.Target%2A> méthode vous permet de récupérer la référence d’objet à partir du handle dans du code managé.

```
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
