---
title: 'Comment : marshaler des chaînes à l’aide de PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: 86ce065da5c214c0da803ad53d19eaec3de5efb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598118"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Comment : marshaler des chaînes à l’aide de PInvoke

Cette rubrique explique comment les fonctions natives qui acceptent des chaînes de style C peuvent être appelées à l’aide de la chaîne CLR System::String à l’aide de la prise en charge de .NET Framework non managé de type. Les programmeurs Visual C++ sont encouragés à utiliser plutôt les fonctionnalités d’interopérabilité C++ (si possible), car P/Invoke peu une erreur de génération de rapports n’est pas de type sécurisé et peut être fastidieuse à implémenter. Si l’API non managée est empaqueté en tant que DLL et le code source n’est pas disponible, P/Invoke est la seule option, mais sinon consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Les chaînes managées et non managées sont disposés différemment en mémoire, par conséquent, le transfert de chaînes à partir de managées nécessite le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour indiquer au compilateur d’insérer les mécanismes de conversion requise pour le marshaling des données de type chaîne correctement et en toute sécurité.

Comme avec les fonctions qui utilisent uniquement des types de données intrinsèques, <xref:System.Runtime.InteropServices.DllImportAttribute> est utilisé pour déclarer des points d’entrée managés dans les fonctions natives mais, pour passer des chaînes au lieu de définir ces points d’entrée comme prenant des chaînes de style C, un handle vers la <xref:System.String> type peut être utilisé à la place. Cela demande au compilateur d’insérer le code qui effectue la conversion nécessaire. Pour chaque argument de fonction dans une fonction non managée qui prend une chaîne, le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut doit être utilisé pour indiquer que l’objet de chaîne doit être marshalée vers la fonction native comme une chaîne de style C.

## <a name="example"></a>Exemple

Le code suivant se compose d’une non managé et un module managé. Le module non managé est une DLL qui définit une fonction appelée TakesAString qui accepte une chaîne de style C ANSI sous la forme d’un char *. Le module managé est une application de ligne de commande qui importe la fonction TakesAString, mais la définit comme prenant un System.String managé au lieu d’un caractère\*. Le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut est utilisé pour indiquer comment la chaîne managée doit être marshalée lorsque TakesAString est appelée.

```
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Cette technique provoque une copie de la chaîne à être construite sur le tas non managé, les modifications apportées à la chaîne par la fonction native n’apparaîtront pas dans la copie de la chaîne managée.

Notez qu’aucune partie de la DLL est exposée au code managé via traditionnel #include, directive. En fait, la DLL est accessible lors de l’exécution uniquement, pour des problèmes avec les fonctions importées avec `DllImport` ne sont pas détectés au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)