---
description: 'En savoir plus sur : utilisation de PInvoke explicite en C++ (attribut DllImport)'
title: Utilisation d'un PInvoke explicite en C++ (attribut DllImport)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: 6c49195cdb677474809435a5bd826808260680e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305466"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Utilisation d'un PInvoke explicite en C++ (attribut DllImport)

Le .NET Framework fournit des fonctionnalités explicites d’appel de code non managé (ou PInvoke) avec l' `Dllimport` attribut pour permettre aux applications managées d’appeler des fonctions non managées empaquetées dans des dll. Un PInvoke explicite est requis pour les situations où les API non managées sont empaquetées en tant que dll et que le code source n’est pas disponible. L’appel de fonctions Win32, par exemple, nécessite PInvoke. Sinon, utilisez implicitement P {Invoke ; pour plus d’informations, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md) .

PInvoke fonctionne à l’aide de <xref:System.Runtime.InteropServices.DllImportAttribute> . Cet attribut, qui prend le nom de la DLL comme premier argument, est placé avant une déclaration de fonction pour chaque point d’entrée de DLL qui sera utilisé. La signature de la fonction doit correspondre au nom d’une fonction exportée par la DLL (mais une conversion de type peut être effectuée implicitement en définissant les `DllImport` déclarations en termes de types managés).

Le résultat est un point d’entrée managé pour chaque fonction DLL native qui contient le code de transition (ou thunk) nécessaire et les conversions de données simples. Les fonctions managées peuvent ensuite appeler la DLL par le biais de ces points d’entrée. Le code inséré dans un module en tant que résultat de PInvoke est entièrement géré.

## <a name="in-this-section"></a>Dans cette section

- [Appel de fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)

- [Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [Comment : marshaler des chaînes à l’aide de PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [Comment : marshaler des structures à l’aide de PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [Comment : marshaler des tableaux à l’aide de PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [Comment : marshaler des pointeurs fonction à l’aide de PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [Comment : marshaler des pointeurs incorporés à l’aide de PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>Voir aussi

[Appel de fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)
