---
title: Intégration CLR (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740292"
---
# <a name="clr-integration-ccx"></a>Intégration CLR (C++/CX)

Certains types de Windows Runtime reçoivent un traitement C++spécial dans/CX et les langages basés sur le Common Language Runtime (CLR). Cet article décrit comment plusieurs types dans un langage sont mappés à un autre langage. Par exemple, le CLR mappe Windows.Foundation.IVector à System.Collections.IList, Windows.Foundation.IMap à System.Collections.IDictionary, et ainsi de suite. De même, C++/CX est spécialement mappé aux types tels que platform ::D délégué et Platform :: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mappage de la Windows Runtime C++à/CX

Quand C++/CX lit un fichier de métadonnées Windows (. winmd), le compilateur mappe automatiquement les types et les espaces C++de noms Windows Runtime communs aux espaces de noms et aux types/CX. Par exemple, le type `UInt32` de Windows Runtime numérique est mappé automatiquement à. `default::uint32`

C++/CX mappe plusieurs autres types de Windows Runtime à l’espace de noms de **plateforme** . Par exemple, le handle **Windows :: Foundation** HSTRING, qui représente une chaîne de texte Unicode en lecture seule, est mappé à la C++classe `Platform::String` /CX. Lorsqu’une opération de Windows Runtime retourne une erreur HRESULT, elle est mappée à C++un `Platform::Exception`/CX.

Le C++/CX mappe également certains types dans Windows Runtime espaces de noms pour améliorer les fonctionnalités du type. Pour ces types, C++/CX fournit des constructeurs et des méthodes d’assistance qui sont spécifiques C++ à et ne sont pas disponibles dans le fichier. winmd standard du type.

Les listes suivantes présentent les structs de valeurs qui prennent en charge les nouvelles méthodes d’assistance et les nouveaux constructeurs. Si vous avez déjà écrit du code qui utilise des listes d’initialisation de struct, modifiez-le pour utiliser les constructeurs qui viennent d’être ajoutés.

**Windows::Foundation**

- Point

- Rect

- Size

**Windows::UI**

- Color

**Windows::UI::Xaml**

- CornerRadius

- Duration

- GridLength

- Thickness

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- Matrix

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mappage du CLR à C++/CX

Lorsque Microsoft C++ ou C# les compilateurs lisent un fichier. winmd, ils mappent automatiquement certains types dans le fichier de métadonnées aux types/CX ou CLR appropriés. C++ Par exemple, dans le CLR, l’interface\<IVector t > est mappée à IList\<t >. Toutefois, C++dans/CX, l'\<interface IVector T > n’est pas mappée à un autre type.

IReference\<t > dans le Windows Runtime est mappé à\<Nullable t > dans .net.

## <a name="see-also"></a>Voir aussi

[Interopérabilité avec d'autres langages](../cppcx/interoperating-with-other-languages-c-cx.md)
