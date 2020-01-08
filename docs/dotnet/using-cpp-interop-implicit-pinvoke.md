---
title: Utilisation de l'interopérabilité C++ (PInvoke implicite)
ms.date: 11/04/2016
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
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676928"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Utilisation de l'interopérabilité C++ (PInvoke implicite)

Contrairement à d’autres langages C++ .net, le visuel a une prise en charge de l’interopérabilité qui permet au code managé et non managé d’exister dans la même application et même dans le même fichier (avec les pragmas [managés et non managés](../preprocessor/managed-unmanaged.md) ). Cela permet aux C++ développeurs visuels d’intégrer les fonctionnalités .net dans C++ les applications visuelles existantes sans perturber le reste de l’application.

Vous pouvez également appeler des fonctions non managées à partir d’un module de configuration managé à l’aide de [dllexport, DllImport](../cpp/dllexport-dllimport.md).

PInvoke implicite est utile lorsque vous n’avez pas besoin de spécifier la manière dont les paramètres de fonction sont marshalés, ou l’un des autres détails qui peuvent être spécifiés lors de l’appel explicite de DllImportAttribute.

Le C++ visuel offre deux moyens pour l’interopérabilité des fonctions managées et non managées :

- [Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Le PInvoke explicite est pris en charge par le .NET Framework et est disponible dans la plupart des langages .NET. Mais comme son nom l’indique C++ , l’interopérabilité est C++spécifique à Visual.

## <a name="c-interop"></a>Interopérabilité C++

C++L’interopérabilité offre une meilleure sécurité des types et il est généralement moins fastidieux à implémenter. Toutefois, C++ l’interopérabilité n’est pas une option si le code source non managé n’est pas disponible ou pour les projets multiplateformes.

## <a name="c-com-interop"></a>interopérabilité C++ COM

Les fonctionnalités d’interopérabilité prises en C++ charge par Visual offrent un avantage particulier par rapport à d’autres langages .NET lorsqu’il s’agit d’interfonctionner avec des composants com. Au lieu d’être limité aux restrictions du .NET Framework [Tlbimp. exe (importateur de bibliothèques de types)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), par exemple la prise en charge limitée des types de données et l’exposition obligatoire de chaque membre C++ de chaque interface com, Interop permet d’accéder à des composants COM à la place et ne requiert pas d’assemblys d’interopérabilité distincts. Contrairement à Visual Basic C#et, C++ Visual peut utiliser des objets com directement à l’aide des mécanismes com habituels (tels que **CoCreateInstance** et **QueryInterface**). Cela est possible en raison C++ des fonctionnalités d’interopérabilité qui obligent le compilateur à insérer automatiquement le code de transition pour passer des fonctions managées à des fonctions non managées, puis de nouveau.

À C++ l’aide de l’interopérabilité, les composants COM peuvent être utilisés tels qu’ils sont normalement C++ utilisés ou ils peuvent être encapsulés dans des classes. Ces classes wrapper sont appelées des wrappers CCW (Runtime Callable Wrapper) personnalisés, ou CRCWs, et elles présentent deux avantages par rapport à l’utilisation directe de COM dans le code de l’application :

- La classe résultante peut être utilisée à partir de langages autres que Visual C++.

- Les détails de l’interface COM peuvent être masqués à partir du code client géré. Les types de données .NET peuvent être utilisés à la place des types natifs, et les détails du marshaling de données peuvent être exécutés de manière transparente à l’intérieur du CRCW.

Même si COM est utilisé directement ou via un CRCW, les types d’argument autres que les types blittables simples doivent être marshalés.

## <a name="blittable-types"></a>Types blittables

Pour les API non managées qui utilisent des types intrinsèques simples (consultez [types blittables et non blittables](/dotnet/framework/interop/blittable-and-non-blittable-types)), aucun codage spécial n’est nécessaire, car ces types de données ont la même représentation en mémoire, mais des types de données plus complexes nécessitent un marshaling de données explicite. Pour obtenir un exemple, consultez [Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

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

- [Comment : convertir System :: String en wchar_t * ou char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Guide pratique pour convertir System::String en chaîne standard](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Guide pratique pour convertir une chaîne standard en System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Guide pratique pour obtenir un pointeur vers un tableau d’octets](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Guide pratique pour charger des ressources non managées dans un tableau d’octets](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Guide pratique pour modifier la classe de référence dans une fonction native](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Guide pratique pour déterminer si une image est native ou CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Guide pratique pour ajouter une DLL native au Global Assembly Cache](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Guide pratique pour stocker une référence à un type valeur dans un type natif](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Guide pratique pour stocker la référence d’un objet dans une mémoire non managée](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Comment : détecter la compilation/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Guide pratique pour procéder à une conversion entre System::Guid et _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Guide pratique pour spécifier un paramètre Out](../dotnet/how-to-specify-an-out-parameter.md)

- [Comment : utiliser un type natif dans une compilation/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Guide pratique pour déclarer des handles dans les types natifs](../dotnet/how-to-declare-handles-in-native-types.md)

- [Guide pratique pour inclure une classe native dans un wrapper pour une utilisation par C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Pour plus d’informations sur l’utilisation de délégués dans un scénario d’interopérabilité, consultez [Delegate (C++ extensions de composant)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Appel à des fonctions natives à partir de code managé](../dotnet/calling-native-functions-from-managed-code.md)
