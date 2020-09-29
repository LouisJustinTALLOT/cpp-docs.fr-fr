---
title: 'Comment : marshaler des chaînes ANSI à l’aide de l’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 3bdffa761bef74b9956842122b913e8213c736e9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414566"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Comment : marshaler des chaînes ANSI à l’aide de l’interopérabilité C++

Cette rubrique montre comment les chaînes ANSI peuvent être transmises à l’aide de l’interopérabilité C++, mais que le .NET Framework <xref:System.String> représente des chaînes au format Unicode. la conversion en ANSI est donc une étape supplémentaire. Pour l’interopérabilité avec d’autres types de chaînes, consultez les rubriques suivantes :

- [Comment : marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Comment : marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais ces fonctions interagissent de la même manière si elles sont définies dans des fichiers distincts. Étant donné que les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), ils peuvent conserver leurs caractéristiques de performances.

## <a name="example-pass-ansi-string"></a>Exemple : Pass ANSI String

L’exemple montre comment passer une chaîne ANSI d’une fonction managée à une fonction non managée à l’aide de <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> . Cette méthode alloue de la mémoire sur le tas non managé et retourne l’adresse après l’exécution de la conversion. Cela signifie qu’aucun épinglage n’est nécessaire (car la mémoire sur le tas GC n’est pas passée à la fonction non managée) et que le IntPtr retourné par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être explicitement libéré ou une fuite de mémoire se produit.

```cpp
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example-data-marshaling-required-to-access-ansi-string"></a>Exemple : marshaling de données requis pour accéder à la chaîne ANSI

L’exemple suivant illustre le marshaling de données requis pour accéder à une chaîne ANSI dans une fonction managée qui est appelée par une fonction non managée. La fonction managée, lors de la réception de la chaîne native, peut l’utiliser directement ou la convertir en chaîne managée à l’aide de la <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> méthode, comme indiqué.

```cpp
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
