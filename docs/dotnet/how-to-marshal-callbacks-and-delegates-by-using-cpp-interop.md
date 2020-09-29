---
title: 'Comment : marshaler des rappels et des délégués à l’aide de l’interopérabilité C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 5d0427962ddb7d6409f07b99c0f618b340ee00df
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414293"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Comment : marshaler des rappels et des délégués à l’aide de l’interopérabilité C++

Cette rubrique décrit le marshaling des rappels et des délégués (la version managée d’un rappel) entre du code managé et du code non managé à l’aide de Visual C++.

Les exemples de code suivants utilisent les directives de #pragma [managées et non managées](../preprocessor/managed-unmanaged.md) pour implémenter des fonctions managées et non managées dans le même fichier, mais les fonctions peuvent également être définies dans des fichiers distincts. Les fichiers contenant uniquement des fonctions non managées n’ont pas besoin d’être compilés avec le [/clr (compilation du Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-configure-unmanaged-api-to-trigger-managed-delegate"></a>Exemple : configurer une API non managée pour déclencher un délégué managé

L’exemple suivant montre comment configurer une API non managée pour déclencher un délégué managé. Un délégué managé est créé et l’une des méthodes d’interopérabilité, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A> , est utilisée pour récupérer le point d’entrée sous-jacent pour le délégué. Cette adresse est ensuite transmise à la fonction non managée, qui l’appelle sans aucune connaissance du fait qu’elle est implémentée en tant que fonction managée.

Notez qu’il est possible, mais pas nécessaire, d’épingler le délégué à l’aide d' [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) pour l’empêcher d’être déplacé ou supprimé par le garbage collector. La protection contre les garbage collection prématurés est nécessaire, mais l’épinglage offre une protection supérieure à celle nécessaire, car elle empêche la collecte mais empêche également la réadressage.

Si un délégué est déplacé par un garbage collection, il n’affecte pas le rappel managé sous-Ponte <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> . il est donc utilisé pour ajouter une référence au délégué, ce qui permet de réadresser le délégué, mais d’empêcher la suppression. L’utilisation de GCHandle au lieu de pin_ptr réduit le potentiel de fragmentation du tas managé.

```cpp
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example-function-pointer-stored-by-unmanaged-api"></a>Exemple : pointeur de fonction stocké par l’API non managée

L’exemple suivant est similaire à l’exemple précédent, mais dans ce cas, le pointeur de fonction fourni est stocké par l’API non managée, de sorte qu’il peut être appelé à tout moment, nécessitant que garbage collection être supprimée pendant une durée arbitraire. Par conséquent, l’exemple suivant utilise une instance globale de <xref:System.Runtime.InteropServices.GCHandle> pour empêcher le délégué d’être déplacé, indépendamment de la portée de la fonction. Comme nous l’avons vu dans le premier exemple, l’utilisation de pin_ptr n’est pas nécessaire pour ces exemples, mais dans ce cas, cela ne fonctionnerait pas quand même, puisque l’étendue d’un pin_ptr est limitée à une seule fonction.

```cpp
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
