---
description: 'En savoir plus sur : intégration du CLR (C++/CX)'
title: Intégration CLR (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: ae335168ee456f0461154ab48e9d92325fdc599b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190235"
---
# <a name="clr-integration-ccx"></a>Intégration CLR (C++/CX)

Certains types de Windows Runtime reçoivent un traitement spécial en C++/CX et les langages basés sur le common language runtime (CLR). Cet article décrit comment plusieurs types dans un langage sont mappés à un autre langage. Par exemple, le CLR mappe Windows.Foundation.IVector à System.Collections.IList, Windows.Foundation.IMap à System.Collections.IDictionary, et ainsi de suite. De même, C++/CX fait spécifiquement correspondre des types tels que Platform ::D délégué et Platform :: String.

## <a name="mapping-the-windows-runtime-to-ccx"></a>Mappage de l’Windows Runtime à C++/CX

Lorsque C++/CX lit un fichier de métadonnées Windows (. winmd), le compilateur mappe automatiquement les types et les espaces de noms Windows Runtime communs aux espaces de noms et aux types C++/CX. Par exemple, le type de Windows Runtime numérique `UInt32` est mappé automatiquement à `default::uint32` .

C++/CX mappe plusieurs autres types de Windows Runtime à l’espace de noms de **plateforme** . Par exemple, le handle **Windows :: Foundation** HSTRING, qui représente une chaîne de texte Unicode en lecture seule, est mappé à la classe C++/CX `Platform::String` . Lorsqu’une opération de Windows Runtime retourne une erreur HRESULT, elle est mappée à un/CX C++ `Platform::Exception` .

Le/CX C++ mappe également certains types dans Windows Runtime espaces de noms pour améliorer les fonctionnalités du type. Pour ces types, C++/CX fournit des constructeurs et des méthodes d’assistance qui sont spécifiques à C++ et qui ne sont pas disponibles dans le fichier. winmd standard du type.

Les listes suivantes présentent les structs de valeurs qui prennent en charge les nouvelles méthodes d’assistance et les nouveaux constructeurs. Si vous avez déjà écrit du code qui utilise des listes d’initialisation de struct, modifiez-le pour utiliser les constructeurs qui viennent d’être ajoutés.

**Windows :: Foundation**

- Point

- Rect

- Taille

**Windows :: UI**

- Couleur

**Windows :: UI :: XAML**

- CornerRadius

- Duration

- GridLength

- Thickness

**Windows::UI::Xaml::Interop**

- TypeName

**Windows :: UI :: XAML :: Media**

- Matrix

**Windows :: UI :: XAML :: Media :: animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>Mappage du CLR à C++/CX

Lorsque les compilateurs Microsoft C++ ou C# lisent un fichier. winmd, ils mappent automatiquement certains types dans le fichier de métadonnées aux types C++/CX ou CLR appropriés. Par exemple, dans le CLR, l' \<T> interface IVector est mappée à IList \<T> . En C++/CX, l’interface IVector \<T> n’est pas mappée à un autre type.

IReference \<T> dans le Windows Runtime est mappé à Nullable \<T> dans .net.

## <a name="see-also"></a>Voir aussi

[Interopérabilité avec d’autres langages](../cppcx/interoperating-with-other-languages-c-cx.md)
