---
title: 'Comment : marshaler des chaînes COM à l’aide d’interopérabilité C++ | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 918825dd6563f59167baa844b94edfc1033498a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133326"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Comment : marshaler des chaînes COM à l’aide de l’interopérabilité C++
Cette rubrique montre comment un BSTR (format de chaîne de base favorisé dans la programmation COM) peut être passé d’une fonction managée à une fonction non managée et vice versa. Pour interagir avec d’autres types de chaînes, consultez les rubriques suivantes :  
  
-   [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 Exemple de code suit le [managé, non managé](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Fichiers contenant uniquement des fonctions non managées ne doivent pas être compilés avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment un BSTR (format de chaîne utilisé dans la programmation COM) peut être passé à partir d’une fonction managée à une fonction non managée. L’appel de fonction utilise managé <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> pour obtenir l’adresse d’une représentation BSTR du contenu d’un System.String .NET. Ce pointeur est épinglé à l’aide de [pin_ptr (C + c++ / CLI)](../windows/pin-ptr-cpp-cli.md) pour vous assurer que son adresse physique n’est pas modifiée pendant un cycle de garbage collection pendant l’exécution de la fonction non managée. Le garbage collector est interdite par le déplacement de la mémoire jusqu'à ce que le [pin_ptr (C + c++ / CLI)](../windows/pin-ptr-cpp-cli.md) est hors de portée.  
  
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
 L’exemple suivant montre comment un BSTR peut être passé à partir d’une fonction non managée à une fonction non managée. La fonction managée peut soit utiliser la chaîne en tant que BSTR ou utilisez la réception <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> pour le convertir en un <xref:System.String> pour une utilisation avec d’autres des fonctions managées. Étant donné que la mémoire représentant le BSTR est allouée sur le tas non managé, aucun épinglage n’est nécessaire, étant donné qu’aucun garbage collection sur le tas non managé.  
  
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