---
description: 'En savoir plus sur : Comment : marshaler des tableaux à l’aide de PInvoke'
title: 'Comment : marshaler des tableaux à l’aide de PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 90fd7b2cbefe2fb3621f512d49fbc088240922a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258221"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Comment : marshaler des tableaux à l’aide de PInvoke

Cette rubrique explique comment des fonctions natives qui acceptent des chaînes de style C peuvent être appelées à l’aide du type de chaîne CLR <xref:System.String> à l’aide de la prise en charge de l’appel de plateforme .NET Framework. Visual C++ les programmeurs sont encouragés à utiliser les fonctionnalités d’interopérabilité C++ à la place (dans la mesure du possible), car P/Invoke fournit peu de rapports d’erreurs de compilation, n’est pas de type sécurisé et peut être fastidieux à implémenter. Si l’API non managée est empaquetée en tant que DLL et que le code source n’est pas disponible, P/Invoke est la seule option (sinon, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).

## <a name="example"></a>Exemple

Étant donné que les tableaux natifs et managés sont disposés différemment en mémoire, leur transmission réussie à travers la limite managée/non managée nécessite une conversion ou un marshaling. Cette rubrique montre comment un tableau d’éléments simples (blitable) peut être passé à des fonctions natives à partir de code managé.

Comme c’est le cas du marshaling de données managées/non managées en général, l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut est utilisé pour créer un point d’entrée managé pour chaque fonction native qui sera utilisée. Dans le cas de fonctions qui prennent des tableaux en tant qu’arguments, l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut doit être utilisé également pour indiquer au compilateur comment les données seront marshalées. Dans l’exemple suivant, l' <xref:System.Runtime.InteropServices.UnmanagedType> énumération est utilisée pour indiquer que le tableau managé sera marshalé en tant que tableau de style C.

Le code suivant est constitué d’un module non managé et d’un module managé. Le module non managé est une DLL qui définit une fonction qui accepte un tableau d’entiers. Le deuxième module est une application de ligne de commande managée qui importe cette fonction, mais la définit en termes de tableau managé et utilise l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour spécifier que le tableau doit être converti en tableau natif lorsqu’il est appelé.

Le module managé est compilé avec/CLR.

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

Notez qu’aucune partie de la DLL n’est exposée au code managé par le biais de la directive #include traditionnelle. En fait, étant donné que la DLL est accessible uniquement au moment de l’exécution, les problèmes liés aux fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
