---
title: "Comment : marshaler des chaînes COM à l'aide de l'interopérabilité C++"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 8dfdad892261d5ae2d3494734458e1447f8ebd7c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988464"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Comment : marshaler des chaînes COM à l'aide de l'interopérabilité C++

Cette rubrique montre comment un BSTR (le format de chaîne de base favorisé dans la programmation COM) peut être passé d’une fonction managée à une fonction non managée, et vice versa. Pour l’interopérabilité avec d’autres types de chaînes, consultez les rubriques suivantes :

- [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment un BSTR (un format de chaîne utilisé dans la programmation COM) peut être passé d’une fonction managée à une fonction non managée. La fonction managée appelante utilise <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> pour obtenir l’adresse d’une représentation BSTR du contenu d’une System. String .NET. Ce pointeur est épinglé à l’aide de [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) pour s’assurer que son adresse physique n’est pas modifiée pendant un cycle de garbage collection pendant l’exécution de la fonction non managée. Le garbage collector est interdit de déplacer la mémoire jusqu’à ce que le [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) soit hors de portée.

```cpp
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

L’exemple suivant montre comment un BSTR peut être passé d’une fonction non managée à une fonction non managée. La fonction managée de réception peut soit utiliser la chaîne dans en tant que BSTR, soit utiliser <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> pour la convertir en <xref:System.String> pour une utilisation avec d’autres fonctions managées. Étant donné que la mémoire représentant le BSTR est allouée sur le tas non managé, aucun épinglage n’est nécessaire, car il n’y a pas de garbage collection sur le tas non managé.

```cpp
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
