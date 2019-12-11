---
title: "Comment : charger des ressources non managées dans un tableau d'octets"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- native resources, loading into Byte array
- unmanaged resources, loading into Byte array
- native resources
ms.assetid: cdada6cd-6d42-437a-a90f-44a0b18d6a93
ms.openlocfilehash: 425def1cd0557298985148d7bb9f74da489643e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988204"
---
# <a name="how-to-load-unmanaged-resources-into-a-byte-array"></a>Comment : charger des ressources non managées dans un tableau d'octets

This topic discusses several ways to load unmanaged resources into a <xref:System.Byte> array.

## <a name="example"></a>Exemple

If you know the size of your unmanaged resource, you can preallocate a CLR array and then load the resource into the array using a pointer to the array block of the CLR array.

```cpp
// load_unmanaged_resources_into_Byte_array.cpp
// compile with: /clr
using namespace System;
void unmanaged_func( unsigned char * p ) {
   for ( int i = 0; i < 10; i++ )
      p[ i ] = i;
}

public ref class A {
public:
   void func() {
      array<Byte> ^b = gcnew array<Byte>(10);
      pin_ptr<Byte> p =  &b[ 0 ];
      Byte * np = p;
      unmanaged_func( np );   // pass pointer to the block of CLR array.
      for ( int i = 0; i < 10; i++ )
         Console::Write( b[ i ] );
      Console::WriteLine();
   }
};

int main() {
   A^ g = gcnew A;
   g->func();
}
```

```Output
0123456789
```

## <a name="example"></a>Exemple

This sample shows how to copy data from an unmanaged memory block to a managed array.

```cpp
// load_unmanaged_resources_into_Byte_array_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <string.h>
int main() {
   char buf[] = "Native String";
   int len = strlen(buf);
   array<Byte> ^byteArray = gcnew array<Byte>(len + 2);

   // convert any native pointer to IntPtr by doing C-Style cast
   Marshal::Copy( (IntPtr)buf, byteArray, 0, len );
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
