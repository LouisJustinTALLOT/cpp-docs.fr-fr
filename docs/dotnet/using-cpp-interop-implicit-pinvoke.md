---
title: À l’aide de l’interopérabilité C++ (PInvoke implicite) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a095f252c4e46e212e42a7ab4cf3cb8d5ef6f53d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704290"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Utilisation de l'interopérabilité C++ (PInvoke implicite)

Contrairement à d’autres langages .NET, Visual C++ est prise en charge de l’interopérabilité qui autorise la présence de code managé et non managé dans la même application et également dans le même fichier (avec le [managé, non managé](../preprocessor/managed-unmanaged.md) pragmas). Cela permet aux développeurs de Visual C++ d’intégrer des fonctionnalités .NET dans les applications Visual C++ existantes sans perturber le reste de l’application.

Vous pouvez également appeler des fonctions non managées à partir d’un module managé à l’aide [dllexport, dllimport](../cpp/dllexport-dllimport.md).

PInvoke implicite est utile lorsque vous n’avez pas besoin de spécifier le mode de marshaling des paramètres de fonction, ou les autres détails qui peuvent être spécifiés lors de l’appel explicite à DllImportAttribute.

Visual C++ fournit des fonctions managées et non managées interagir de deux façons :

- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Un PInvoke explicite est pris en charge par le .NET Framework et n’est disponible dans la plupart des langages .NET. Cependant, comme son nom l’indique, C++ Interop est spécifique à Visual C++.

## <a name="c-interop"></a>Interopérabilité C++

Interopérabilité C++ est recommandée sur un PInvoke explicite, car il assure une meilleure sécurité de type, est généralement moins fastidieux à implémenter, est plus indulgent si l’API non managée est modifié et rend les améliorations des performances qui ne sont pas possibles avec explicite PInvoke. Toutefois, l’interopérabilité C++ n’est pas possible si le code source non managé n’est pas disponible.

## <a name="c-com-interop"></a>interopérabilité C++ COM

Les fonctionnalités d’interopérabilité prises en charge par Visual C++ procurent un avantage particulier par rapport aux autres langages .NET lorsqu’il s’agit de l’interopérabilité avec les composants COM. Au lieu d’être limité aux restrictions du .NET Framework [Tlbimp.exe (Type Library Importer)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), telles que la prise en charge limitée pour les types de données et l’exposition obligatoire de chaque membre de chaque interface COM, C++ Interop autorise COM y accéder à des composants sera et ne nécessite pas d’assemblys d’interopérabilité distincts. Contrairement à Visual Basic et c#, Visual C++ peut utiliser des objets COM directement à l’aide des mécanismes COM habituels (tels que **CoCreateInstance** et **QueryInterface**). Cela est possible en raison des fonctionnalités d’interopérabilité C++ qui provoquent le compilateur insère automatiquement le code de transition pour déplacer à partir de fonctions managées et vice versa.

Utiliser l’interopérabilité C++, les composants de COM peuvent être utilisés comme ils sont normalement utilisés ou ils peuvent être encapsulés dans des classes C++. Ces classes wrapper sont appelées wrappers RCW personnalisé, ou CRCW et possèdent deux avantages par rapport à l’aide de COM directement dans le code d’application :

- La classe résultante peut être utilisée à partir de langages autres que Visual C++.

- Les détails de l’interface COM peuvent être masqués à partir du code client géré. Types de données .NET peuvent être utilisés à la place des types natifs, et les détails de marshaling de données peuvent être effectuées de manière transparente à l’intérieur du CRCW.

Quelle que soit la COM soit utilisé directement ou via un CRCW, types d’arguments autres que des types simples blittables doivent être marshalés.

## <a name="blittable-types"></a>Types blittables

Pour les API non managées qui utilisent des types intrinsèques simples (consultez [Types blittables et Non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun codage spécial n’est requis, car ces types de données ont la même représentation en mémoire, mais nécessitent des types de données plus complexes. marshaling de données explicites. Pour obtenir un exemple, consultez [Comment : appeler des DLL natives à partir de PInvoke d’à l’aide de Code managé](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

## <a name="example"></a>Exemple

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>Dans cette section

- [Guide pratique pour marshaler des chaînes ANSI à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes Unicode à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des chaînes COM à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [Guide pratique pour marshaler des structures à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [Guide pratique pour marshaler des tableaux à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [Guide pratique pour marshaler des rappels et des délégués à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Guide pratique pour marshaler des pointeurs incorporés à l’aide de l’interopérabilité C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Guide pratique pour accéder aux caractères d’un System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Guide pratique pour convertir la chaîne char * en tableau System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Comment : convertir System::String en wchar_t * ou char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Guide pratique pour convertir System::String en chaîne standard](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Guide pratique pour convertir une chaîne standard en System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Guide pratique pour obtenir un pointeur vers un tableau d’octets](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Guide pratique pour charger des ressources non managées dans un tableau d’octets](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Guide pratique pour modifier la classe de référence dans une fonction native](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Guide pratique pour déterminer si une image est native ou CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Guide pratique pour ajouter une DLL native au Global Assembly Cache](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Guide pratique pour stocker une référence à un type valeur dans un type natif](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Guide pratique pour stocker la référence d’un objet dans une mémoire non managée](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Comment : détecter une Compilation /clr](../dotnet/how-to-detect-clr-compilation.md)

- [Guide pratique pour procéder à une conversion entre System::Guid et _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Guide pratique pour spécifier un paramètre Out](../dotnet/how-to-specify-an-out-parameter.md)

- [Comment : utiliser un Type natif dans une Compilation /clr](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Guide pratique pour déclarer des handles dans les types natifs](../dotnet/how-to-declare-handles-in-native-types.md)

- [Guide pratique pour inclure une classe native dans un wrapper pour une utilisation par C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Pour plus d’informations sur l’utilisation de délégués dans un scénario d’interopérabilité, consultez [delegate (Extensions du composant C++)](../windows/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Appel à des fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)
