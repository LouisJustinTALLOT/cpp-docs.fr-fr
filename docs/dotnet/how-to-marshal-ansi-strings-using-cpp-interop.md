---
title: "Comment : marshaler des chaînes ANSI à l’aide d’interopérabilité C++ | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e70d62fa7a94a7278080c31f6650b31b71ff35b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Comment : marshaler des chaînes ANSI à l’aide de l’interopérabilité C++
Cette rubrique montre comment les chaînes ANSI peuvent être passées à l’aide de C++ Interop, mais le .NET Framework <xref:System.String> représente des chaînes au format Unicode, par conséquent, la conversion au format ANSI est une étape supplémentaire. Pour interagir avec d’autres types de chaîne, consultez les rubriques suivantes :  
  
-   [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Guide pratique pour marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 Exemple de code suit le [managé, non managé](../preprocessor/managed-unmanaged.md) directives #pragma pour implémenter des fonctions managées et dans le même fichier, mais ces fonctions interagissent de la même manière, si elles sont définies dans des fichiers distincts. Étant donné que les fichiers contenant uniquement des fonctions non managées ne doivent pas être compilés avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), ils peuvent conserver leurs caractéristiques de performances.  
  
## <a name="example"></a>Exemple  
 L’exemple illustre le passage d’une chaîne ANSI d’une fonction managée à une fonction non managée à l’aide <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Cette méthode alloue de la mémoire sur le tas non managé et retourne l’adresse après la conversion. Cela signifie qu’aucun épinglage n’est nécessaire (car la mémoire sur le tas GC n’est pas passée à la fonction non managée) et que la valeur IntPtr retournée à partir de <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> doit être explicitement libéré ou une fuite des résultats de la mémoire.  
  
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
 L’exemple suivant illustre le marshaling de données requis pour accéder à une chaîne ANSI dans une fonction managée est appelée par une fonction non managée. Lors de la réception de la chaîne native, la fonction managée peut utiliser directement ou la convertir en une chaîne managée à l’aide de la <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> méthode, comme indiqué.  
  
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