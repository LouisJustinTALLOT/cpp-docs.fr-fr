---
title: 'Comment : marshaler des pointeurs à l’aide de PInvoke incorporés | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a07c9742c393abe2a6213378ee8963839ab66c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134895"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Comment : marshaler des pointeurs incorporés à l’aide de PInvoke
Les fonctions qui sont implémentées dans des DLL non managées peuvent être appelées à partir du code managé à l’aide de la fonctionnalité de code non managé (P/Invoke). Si le code source pour la DLL n’est pas disponible, P/Invoke est la seule option pour l’interopérabilité. Toutefois, contrairement à d’autres langages .NET, Visual C++ fournit une alternative à P/Invoke. Pour plus d’informations, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md) et [Comment : marshaler incorporées des pointeurs à l’aide de C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
## <a name="example"></a>Exemple  
 Passage de structures en code natif requiert qu’une structure managée équivalent en termes de mise en page de données à la structure native est créée. Toutefois, les structures qui contiennent des pointeurs requièrent un traitement spécial. Pour chaque pointeur incorporé dans la structure native, la version managée de la structure doit contenir une instance de la <xref:System.IntPtr> type. En outre, mémoire pour ces instances doivent être allouées de manière explicite, initialisé et publié à l’aide de la <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, et <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> méthodes.  
  
 Le code suivant se compose d’une fonction non managée et un module managé. Le module non managé est une DLL qui définit une fonction qui accepte une structure appelée ListString qui contient un pointeur et une fonction appelée TakesListStruct. Le module managé est une application de ligne de commande qui importe la fonction TakesListStruct et définit une structure appelée MListStruct équivalant au ListStruct natif, mais où le double * est représenté par un <xref:System.IntPtr> instance. Avant d’appeler TakesListStruct, la fonction principale alloue et initialise la mémoire qui fait référence à ce champ.  
  
```cpp  
// TraditionalDll6.cpp  
// compile with: /EHsc /LD  
#include <stdio.h>  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct ListStruct {  
   int count;  
   double* item;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API void TakesListStruct(ListStruct);  
}  
  
void TakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
```  
  
```cpp  
// EmbeddedPointerMarshalling.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MListStruct {  
   int count;  
   IntPtr item;  
};  
  
value struct TraditionalDLL {  
    [DllImport("TraditionalDLL6.dll")]  
   static public void TakesListStruct(MListStruct);  
};  
  
int main() {  
   array<double>^ parray = gcnew array<double>(10);  
   Console::WriteLine("[managed] count = {0}", parray->Length);  
  
   Random^ r = gcnew Random();  
   for (int i=0; i<parray->Length; i++) {  
      parray[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);  
   }  
  
   int size = Marshal::SizeOf(double::typeid);  
   MListStruct list;  
   list.count = parray->Length;  
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);  
  
   for (int i=0; i<parray->Length; i++) {  
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);  
      Marshal::StructureToPtr(parray[i], t, false);  
   }  
  
   TraditionalDLL::TakesListStruct( list );  
   Marshal::FreeCoTaskMem(list.item);  
}  
```  
  
 Notez qu’aucune partie de la DLL est exposée au code managé à l’aide de traditionnel #include (directive). En fait, la DLL est accessible au moment de l’exécution pour les problèmes liés aux fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)