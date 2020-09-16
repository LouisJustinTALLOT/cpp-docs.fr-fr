---
title: "Comment : accéder aux caractères d'un System::String"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: cb62eb0fecbee202e4d01635a60da565241822ee
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686793"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Comment : accéder aux caractères d'un System::String

Vous pouvez accéder aux caractères d’un <xref:System.String> objet pour les appels hautes performances aux fonctions non managées qui acceptent des `wchar_t*` chaînes. La méthode génère un pointeur intérieur vers le premier caractère de l' <xref:System.String> objet. Ce pointeur peut être manipulé directement ou épinglé et passé à une fonction qui attend une **`wchar_t`** chaîne ordinaire.

## <a name="examples"></a>Exemples

`PtrToStringChars` retourne un <xref:System.Char> , qui est un pointeur intérieur (également appelé `byref` ). En tant que tel, il est soumis à garbage collection. Vous n’êtes pas obligé d’épingler ce pointeur à moins que vous ne le passiez à une fonction native.

Prenons le code suivant.  L’épinglage n’est pas nécessaire, car `ppchar` est un pointeur intérieur et, si le garbage collector déplace la chaîne vers laquelle il pointe, il est également mis à jour `ppchar` . Sans [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md), le code fonctionnera et n’aura pas d’impact sur les performances potentielles causées par l’épinglage.

Si vous transmettez `ppchar` à une fonction native, il doit s’agir d’un pointeur épingle ; le garbage collector ne sera pas en mesure de mettre à jour les pointeurs sur le frame de pile non managé.

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

Cet exemple montre où l’épinglage est nécessaire.

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

Un pointeur intérieur a toutes les propriétés d’un pointeur C++ natif. Par exemple, vous pouvez l’utiliser pour parcourir une structure de données liées et effectuer des insertions et des suppressions à l’aide d’un seul pointeur :

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
