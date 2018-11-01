---
title: 'Comment : marshaler des chaînes COM à l’aide de l’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 664c9ed973e2dff4467d13742390da8a944eb87a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559118"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Comment : marshaler des chaînes COM à l’aide de l’interopérabilité C++

Cette rubrique montre comment un BSTR (format de chaîne de base favorisé dans la programmation COM) peut être passé d’une fonction managée à une fonction non managée et vice versa. Pour interagir avec d’autres types de chaînes, consultez les rubriques suivantes :

- [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Exemple de code suit le [managed, unmanaged](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Fichiers contenant uniquement des fonctions non managées ne doivent pas être compilé avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment un BSTR (format de chaîne utilisé dans la programmation COM) peut être passé à partir d’une fonction managée à une fonction non managée. L’appel de fonction utilise managé <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> pour obtenir l’adresse d’une représentation BSTR du contenu d’un System.String .NET. Ce pointeur est épinglé à l’aide de [pin_ptr (C++ / c++ / CLI)](../windows/pin-ptr-cpp-cli.md) pour vous assurer que son adresse physique n’est pas modifiée pendant un cycle de garbage collection pendant que la fonction non managée s’exécute. Le garbage collector est pas autorisé à déplacer la mémoire jusqu'à ce que le [pin_ptr (C++ / c++ / CLI)](../windows/pin-ptr-cpp-cli.md) est hors de portée.

```
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment un BSTR peut être passé à partir d’une fonction non managée à une fonction non managée. La réception fonction managée peut utiliser la chaîne en tant que BSTR ou <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> à convertir en un <xref:System.String> pour une utilisation avec d’autres les fonctions managées. Étant donné que la mémoire représentant le BSTR est allouée sur le tas non managé, aucun épinglage n’est nécessaire, car il n’existe aucun garbage collection sur le tas non managé.

```
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)