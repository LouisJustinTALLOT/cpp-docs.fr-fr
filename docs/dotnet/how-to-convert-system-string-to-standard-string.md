---
description: 'En savoir plus sur : Comment : convertir System :: String en chaîne standard'
title: 'Comment : convertir System::String en chaîne standard'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, converting System::String to standard string
- string conversion, System::String
ms.assetid: 79e2537e-d4eb-459f-9506-0e738045b59e
ms.openlocfilehash: 2bcdaef743f2856f2db20dae8b804bb33546ea0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181329"
---
# <a name="how-to-convert-systemstring-to-standard-string"></a>Comment : convertir System::String en chaîne standard

Vous pouvez convertir <xref:System.String> en `std::string` ou `std::wstring` , sans utiliser `PtrToStringChars` dans Vcclr. h.

## <a name="example"></a>Exemple

```cpp
// convert_system_string.cpp
// compile with: /clr
#include <string>
#include <iostream>
using namespace std;
using namespace System;

void MarshalString ( String ^ s, string& os ) {
   using namespace Runtime::InteropServices;
   const char* chars =
      (const char*)(Marshal::StringToHGlobalAnsi(s)).ToPointer();
   os = chars;
   Marshal::FreeHGlobal(IntPtr((void*)chars));
}

void MarshalString ( String ^ s, wstring& os ) {
   using namespace Runtime::InteropServices;
   const wchar_t* chars =
      (const wchar_t*)(Marshal::StringToHGlobalUni(s)).ToPointer();
   os = chars;
   Marshal::FreeHGlobal(IntPtr((void*)chars));
}

int main() {
   string a = "test";
   wstring b = L"test2";
   String ^ c = gcnew String("abcd");

   cout << a << endl;
   MarshalString(c, a);
   c = "efgh";
   MarshalString(c, b);
   cout << a << endl;
   wcout << b << endl;
}
```

```Output
test
abcd
efgh
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
