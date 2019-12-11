---
title: 'Comment : marshaler des chaînes Unicode à l’aide de l’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f666e52b604e4713f02cb14744ac12a0407366a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988164"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Comment : marshaler des chaînes Unicode à l’aide de l’interopérabilité C++

Cette rubrique présente une facette de C++ l’interopérabilité visuelle. Pour plus d’informations, [consultez C++ utilisation de l’interopérabilité (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Cette rubrique montre comment passer des chaînes Unicode d’une fonction managée à une fonction non managée, et vice versa. Pour l’interopérabilité avec d’autres types de chaînes, consultez les rubriques suivantes :

- [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Exemple

Pour passer une chaîne Unicode d’une fonction managée à une fonction non managée, la fonction PtrToStringChars (déclarée dans Vcclr. h) peut être utilisée pour accéder à la mémoire où la chaîne managée est stockée. Étant donné que cette adresse sera transmise à une fonction native, il est important que la mémoire soit épinglée avec [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) pour empêcher que les données de chaîne ne soient déplacées, si un cycle de garbage collection a lieu pendant l’exécution de la fonction non managée.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Exemple

L’exemple suivant illustre le marshaling de données requis pour accéder à une chaîne Unicode dans une fonction managée appelée par une fonction non managée. La fonction managée, lors de la réception de la chaîne Unicode native, la convertit en chaîne managée à l’aide de la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>.

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
