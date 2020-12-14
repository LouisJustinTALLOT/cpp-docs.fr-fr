---
description: 'En savoir plus sur : Comment : marshaler des pointeurs de fonction à l’aide de PInvoke'
title: "Comment : marshaler des pointeurs fonction à l'aide de PInvoke"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: bfe3f669cf023ed914bdccb3ae15ccafefbb49c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302580"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Comment : marshaler des pointeurs fonction à l'aide de PInvoke

Cette rubrique explique comment utiliser les délégués managés à la place des pointeurs de fonction lors de l’interopérabilité avec les fonctions non managées à l’aide de .NET Framework fonctionnalités P/Invoke. Toutefois, Visual C++ programmeurs sont encouragés à utiliser les fonctionnalités d’interopérabilité C++ à la place (dans la mesure du possible), car P/Invoke fournit peu de rapports d’erreurs de compilation, n’est pas de type sécurisé et peut être fastidieux à implémenter. Si l’API non managée est empaquetée en tant que DLL et que le code source n’est pas disponible, P/Invoke est la seule option. Dans le cas contraire, consultez les rubriques suivantes :

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Comment : marshaler des rappels et des délégués à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

Les API non managées qui prennent des pointeurs de fonction en tant qu’arguments peuvent être appelées à partir du code managé avec un délégué managé au lieu du pointeur de fonction natif. Le compilateur marshale automatiquement le délégué en fonctions non managées en tant que pointeur de fonction et insère le code de transition managé/non managé nécessaire.

## <a name="example"></a>Exemple

Le code suivant est constitué d’un module non managé et d’un module managé. Le module non managé est une DLL qui définit une fonction appelée TakesCallback qui accepte un pointeur de fonction. Cette adresse est utilisée pour exécuter la fonction.

Le module managé définit un délégué qui est marshalé en code natif en tant que pointeur de fonction et utilise l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut pour exposer la fonction TakesCallback Native au code managé. Dans la fonction main, une instance du délégué est créée et transmise à la fonction TakesCallback. La sortie du programme démontre que cette fonction est exécutée par la fonction TakesCallback native.

La fonction managée supprime garbage collection pour le délégué managé afin d’empêcher .NET Framework garbage collection de déplacer le délégué pendant l’exécution de la fonction native.

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

Notez qu’aucune partie de la DLL n’est exposée au code managé à l’aide de la directive #include traditionnelle. En fait, la DLL est accessible uniquement au moment de l’exécution. par conséquent, les problèmes liés aux fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
