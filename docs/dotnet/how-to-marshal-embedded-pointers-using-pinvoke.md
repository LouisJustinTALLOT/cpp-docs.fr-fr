---
description: 'En savoir plus sur : Comment : marshaler des pointeurs incorporés à l’aide de PInvoke'
title: 'Comment : marshaler des pointeurs incorporés à l’aide de PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: d31660a9a8ba345b380d442bb4484e332fe9d7cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302554"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Comment : marshaler des pointeurs incorporés à l’aide de PInvoke

Les fonctions implémentées dans des dll non managées peuvent être appelées à partir du code managé à l’aide de la fonctionnalité d’appel de code non managé (P/Invoke). Si le code source de la DLL n’est pas disponible, P/Invoke est la seule option pour l’interopérabilité. Toutefois, contrairement à d’autres langages .NET, Visual C++ fournit une alternative à P/Invoke. Pour plus d’informations, consultez [utilisation de l’interopérabilité c++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md) et [Comment : marshaler des pointeurs incorporés à l’aide de l’interopérabilité c++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

## <a name="example"></a>Exemple

Le passage de structures au code natif requiert la création d’une structure managée qui est équivalente en termes de disposition des données à la structure native. Toutefois, les structures qui contiennent des pointeurs nécessitent un traitement spécial. Pour chaque pointeur incorporé dans la structure native, la version managée de la structure doit contenir une instance du <xref:System.IntPtr> type. En outre, la mémoire de ces instances doit être explicitement allouée, initialisée et libérée à l’aide des <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A> <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A> méthodes, et <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> .

Le code suivant est constitué d’un module non managé et d’un module managé. Le module non managé est une DLL qui définit une fonction qui accepte une structure appelée ListString qui contient un pointeur et une fonction appelée TakesListStruct. Le module managé est une application de ligne de commande qui importe la fonction TakesListStruct et définit une structure appelée MListStruct qui est équivalente à la ListStruct native, à l’exception du fait que le double * est représenté par une <xref:System.IntPtr> instance. Avant d’appeler TakesListStruct, la fonction main alloue et initialise la mémoire référencée par ce champ.

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

Notez qu’aucune partie de la DLL n’est exposée au code managé à l’aide de la directive #include traditionnelle. En fait, la DLL est accessible uniquement au moment de l’exécution. par conséquent, les problèmes liés aux fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
