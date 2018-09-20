---
title: 'Comment : marshaler des chaînes ANSI à l’aide de C++ Interop | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4a1a0cd8b9da5812e404f70dc999dfaf1606666
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383361"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Comment : marshaler des chaînes ANSI à l’aide de l’interopérabilité C++

Cette rubrique montre comment les chaînes ANSI peuvent être passées à l’aide de C++ Interop, mais le .NET Framework <xref:System.String> représente des chaînes au format Unicode, par conséquent, la conversion en ANSI est une étape supplémentaire. Pour interagir avec d’autres types de chaîne, consultez les rubriques suivantes :

- [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Exemple de code suit le [managed, unmanaged](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Étant donné que les fichiers contenant uniquement des fonctions non managées ne doivent pas être compilé avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), ils peuvent conserver leurs caractéristiques de performances.

## <a name="example"></a>Exemple

L’exemple illustre le passage d’une chaîne ANSI d’une fonction managée à une fonction non managée à l’aide <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Cette méthode alloue de la mémoire sur le tas non managé et retourne l’adresse après la conversion. Cela signifie qu’aucun épinglage n’est nécessaire (car la mémoire sur le tas GC n’est pas passée à la fonction non managée) et que le pointeur IntPtr retournée par <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être explicitement libéré ou une fuite des résultats de la mémoire.

```
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

## <a name="example"></a>Exemple

L’exemple suivant illustre le marshaling de données nécessaire pour accéder à une chaîne ANSI dans une fonction managée appelée par une fonction non managée. La fonction managée, à la réception de la chaîne native, pouvez utiliser directement ou convertissez-la en une chaîne managée à l’aide de la <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> méthode, comme indiqué.

```
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