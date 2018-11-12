---
title: 'Comment : marshaler des pointeurs fonction à l’aide de PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 2f12c86b7e32955622a4a2c598d01057e303a329
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435605"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Comment : marshaler des pointeurs fonction à l’aide de PInvoke

Cette rubrique explique comment les délégués managés peut être utilisé à la place des pointeurs de fonction lors de l’interaction avec l’utilisation des fonctionnalités de .NET Framework P/Invoke de fonctions non managées. Toutefois, les programmeurs Visual C++ sont encouragés à utiliser plutôt les fonctionnalités d’interopérabilité C++ (si possible), car P/Invoke peu une erreur de génération de rapports n’est pas de type sécurisé et peut être fastidieuse à implémenter. Si l’API non managée est empaqueté en tant que DLL et le code source n’est pas disponible, P/Invoke est la seule option. Sinon, consultez les rubriques suivantes :

- [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Guide pratique pour marshaler des rappels et des délégués à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

Les API non managées qui prennent des pointeurs de fonctions comme arguments peuvent être appelées à partir du code managé avec un délégué managé à la place le pointeur de fonction native. Le compilateur automatiquement marshale le délégué à des fonctions non managées comme un pointeur de fonction et insère le code de transition managés/non managés non nécessaire.

## <a name="example"></a>Exemple

Le code suivant se compose d’une fonction non managée et un module managé. Le module non managé est une DLL qui définit une fonction appelée TakesCallback qui accepte un pointeur de fonction. Cette adresse est utilisée pour exécuter la fonction.

Le module managé définit un délégué est marshalé en code natif en tant que pointeur fonction et utilise le <xref:System.Runtime.InteropServices.DllImportAttribute> attribut pour exposer la fonction TakesCallback native du code managé. Dans la fonction principale, une instance du délégué est créée et transmise à la fonction TakesCallback. La sortie du programme montre que cette fonction est exécutée par la fonction TakesCallback native.

La fonction managée supprime le garbage collection pour le délégué managé empêcher le garbage collection du .NET Framework de déplacer le délégué pendant que la fonction native s’exécute.

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

Notez qu’aucune partie de la DLL est exposée au code managé à l’aide de traditionnel #include, directive. En fait, la DLL est accessible au moment de l’exécution pour des problèmes avec les fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)