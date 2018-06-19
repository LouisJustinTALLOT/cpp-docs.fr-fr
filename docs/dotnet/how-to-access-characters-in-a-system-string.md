---
title: 'Comment : accéder aux caractères d’un System::String | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed9682492eedc915919758d42d5594560cb4a83a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129747"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Comment : accéder aux caractères d'un System::String
Vous pouvez accéder aux caractères d’un <xref:System.String> des fonctions de l’objet pour les appels de hautes performances à non managé utilisant `wchar_t*` chaînes. La méthode génère un pointeur intérieur vers le premier caractère de la <xref:System.String> objet. Ce pointeur peut être manipulé directement ou épinglé et passé à une fonction qui attend un ordinaire `wchar_t` chaîne.  
  
## <a name="example"></a>Exemple  
 `PtrToStringChars` Retourne un <xref:System.Char>, qui est un pointeur intérieur (également appelé un `byref`). Par conséquent, il est soumis au garbage collection. Vous n’êtes pas obligé d’épingler ce pointeur à moins que vous allez passer à une fonction native.  
  
 Prenons le code suivant.  L’épinglage n’est pas nécessaire, car `ppchar` est un pointeur intérieur, et si le garbage collector déplace la chaîne vers laquelle il pointe, il met également à jour `ppchar`. Sans un [pin_ptr (C + c++ / CLI)](../windows/pin-ptr-cpp-cli.md), le code fonctionnera, et pas le gain de performances potentiels ont provoqué par l’épinglage.  
  
 Si vous passez `ppchar` à une fonction native, il doit être un pointeur épingle ; le garbage collector ne sera pas en mesure de mettre à jour tous les pointeurs sur le frame de pile non managé.  
  
```  
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
  
## <a name="example"></a>Exemple  
 Cet exemple montre où l’épinglage est nécessaire.  
  
```  
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
  
## <a name="example"></a>Exemple  
 Un pointeur intérieur possède toutes les propriétés d’un pointeur C++ natif. Par exemple, vous pouvez l’utiliser pour parcourir une structure de données liées et effectuer des insertions et suppressions à l’aide uniquement un pointeur :  
  
```  
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