---
title: Utilisation d'un PInvoke explicite en C++ (attribut DllImport)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: ee9d77920f04f7eba5112c66a906b02b7fc4a658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384424"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Utilisation d'un PInvoke explicite en C++ (attribut DllImport)

Le .NET Framework fournit des fonctionnalités de code non managé (ou PInvoke) explicites avec le `Dllimport` attribut pour autoriser les applications gérées d’appeler des fonctions non managées empaquetées à l’intérieur de DLL. Un PInvoke explicite est requis pour les situations où les API non managées sont empaquetés en tant que DLL et le code source n’est pas disponible. Appel de fonctions Win32, par exemple, nécessite de PInvoke. Sinon, utilisez P implicite {Invoke ; consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md) pour plus d’informations.

PInvoke fonctionne à l’aide de <xref:System.Runtime.InteropServices.DllImportAttribute>. Cet attribut, qui prend le nom de la DLL comme premier argument, est placé avant une déclaration de fonction pour chaque point d’entrée DLL qui sera utilisé. La signature de la fonction doit correspondre au nom d’une fonction exportée par la DLL (mais une conversion de type peut être exécutée implicitement en définissant le `DllImport` déclarations en termes de types managés.)

Le résultat est un point d’entrée managé pour chaque fonction DLL native qui contient le code de transition nécessaire (ou thunk) et les conversions de données simples. Fonctions managées peuvent ensuite appeler la DLL via ces points d’entrée. Le code inséré dans un module en tant que résultat de PInvoke est entièrement géré.

## <a name="in-this-section"></a>Dans cette section

- [Appel à des fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)

- [Guide pratique pour appeler des DLL natives à partir du code managé à l’aide de PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [Guide pratique pour marshaler des chaînes à l’aide de PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [Guide pratique pour marshaler des structures à l’aide de PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [Guide pratique pour marshaler des tableaux à l’aide de PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [Guide pratique pour marshaler des pointeurs fonction à l’aide de PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [Guide pratique pour marshaler des pointeurs incorporés à l’aide de PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>Voir aussi

[Appel à des fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)
