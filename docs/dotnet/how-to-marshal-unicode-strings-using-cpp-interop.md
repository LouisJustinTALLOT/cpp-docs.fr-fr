---
title: 'Procédure : Marshaler des chaînes Unicode à l’aide d’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 37b56834e000cff686557730252f3d425f642772
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777673"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Procédure : Marshaler des chaînes Unicode à l’aide d’interopérabilité C++

Cette rubrique illustre une facette de l’interopérabilité de Visual C++. Pour plus d’informations, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Exemple de code suit le [managed, unmanaged](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Fichiers contenant uniquement des fonctions non managées ne doivent pas être compilé avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Cette rubrique montre comment les chaînes Unicode peuvent être passé d’une fonction managée à une fonction non managée et vice versa. Pour interagir avec d’autres types de chaînes, consultez les rubriques suivantes :

- [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Exemple

Pour transmettre une chaîne Unicode d’une fonction managée à une fonction non managée, la fonction PtrToStringChars (déclarée dans Vcclr.h) peut être utilisée pour accéder à la mémoire où la chaîne managée est stockée. Étant donné que cette adresse doit être passée à une fonction native, il est important que la mémoire soit épinglée avec [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) pour empêcher que les données de chaîne ne soient déplacées, devrait un cycle de garbage collection se produire lors de la fonction non managée s’exécute.

```
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

L’exemple suivant illustre le marshaling de données requis pour accéder à une chaîne Unicode dans une fonction managée appelée par une fonction non managée. La fonction managée, reçoit la chaîne Unicode native, il convertit en une chaîne managée à l’aide de la <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> (méthode).

```
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
