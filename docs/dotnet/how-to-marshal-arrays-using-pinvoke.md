---
title: 'Comment : marshaler des tableaux à l’aide de PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c07aba54f621011d2dd4831d7dfb6b536073fa9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395685"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Comment : marshaler des tableaux à l’aide de PInvoke

Cette rubrique explique comment les fonctions natives qui acceptent des chaînes de style C peuvent être appelées en utilisant le type de chaîne CLR <xref:System.String> à l’aide de la prise en charge de .NET Framework non managé. Les programmeurs Visual C++ sont encouragés à utiliser plutôt les fonctionnalités d’interopérabilité C++ (si possible), car P/Invoke peu une erreur de génération de rapports n’est pas de type sécurisé et peut être fastidieuse à implémenter. Si l’API non managée est empaqueté en tant que DLL et le code source n’est pas disponible, P/Invoke est la seule option (sinon, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).

## <a name="example"></a>Exemple

Étant donné que les tableaux natifs et managés sont disposés différemment en mémoire, leur passage entre la limite managée/nécessite la conversion ou un marshaling. Cette rubrique montre comment un tableau d’éléments de simples (blittables) peut être passé aux fonctions natives à partir du code managé.

De même non managé de marshaling de données en général, le <xref:System.Runtime.InteropServices.DllImportAttribute> attribut est utilisé pour créer un point d’entrée managé pour chaque fonction native qui sera utilisé. Dans le cas des fonctions qui acceptent les tableaux en tant qu’arguments, le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut doit être utilisé pour spécifier au compilateur comment les données doivent être marshalées. Dans l’exemple suivant, le <xref:System.Runtime.InteropServices.UnmanagedType> énumération est utilisée pour indiquer que le tableau managé doit être marshalé en tant qu’un tableau de style C.

Le code suivant se compose d’une fonction non managée et un module managé. Le module non managé est une DLL qui définit une fonction qui accepte un tableau d’entiers. Le deuxième module est une application de ligne de commande managée qui importe cette fonction, mais il définit en termes d’un tableau managé et utilise le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour spécifier que le tableau doit être converti en un tableau natif lorsqu’elle est appelée.

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

Notez qu’aucune partie de la DLL est exposée au code managé via traditionnel #include, directive. En fait, étant donné que la DLL est accessible au moment de l’exécution, des problèmes avec les fonctions importées avec <xref:System.Runtime.InteropServices.DllImportAttribute> ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)