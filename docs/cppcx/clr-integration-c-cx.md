---
title: Intégration du CLR (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d75b8cb328ec69d5c322538a073fac5fc1761aed
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683676"
---
# <a name="clr-integration-ccx"></a>Intégration CLR (C++/CX)
Certains types de Runtime de Windows reçoivent un traitement spécial en C / c++ / CX et les langues qui sont basées sur le common language runtime (CLR). Cet article décrit comment plusieurs types dans un langage sont mappés à un autre langage. Par exemple, le CLR mappe Windows.Foundation.IVector à System.Collections.IList, Windows.Foundation.IMap à System.Collections.IDictionary, et ainsi de suite. De même, C++ / c++ / CX mappe spécialement des types tels que Platform::Delegate et Platform::String.  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>Mappage de l’exécution de Windows à C++ / c++ / CX  
 Lorsque C++ / c++ / CX lit un fichier de métadonnées (.winmd) Windows, le compilateur mappe automatiquement les types et les espaces de noms communs Windows Runtime C + c++ / CX espaces de noms et types. Par exemple, le type Windows Runtime numérique `UInt32` est automatiquement mappé à `default::uint32`.  
  
 C++ / c++ / CX mappe plusieurs autres types Windows Runtime pour le **plateforme** espace de noms. Par exemple, le **Windows::Foundation** handle HSTRING, qui représente une chaîne de texte Unicode en lecture seule, est mappé à C++ / c++ / CX `Platform::String` classe. Lorsqu’une opération Windows Runtime retourne une erreur HRESULT, il est mappé à un C + c++ / CX `Platform::Exception`.   
  
 C++ / c++ / CX mappe également certains types dans les espaces de noms Windows Runtime pour améliorer les fonctionnalités du type. Pour ces types, C++ / c++ / CX fournit des constructeurs d’assistance et des méthodes qui sont spécifiques à C++ et ne sont pas disponibles dans le fichier du type .winmd standard.  
  
 Les listes suivantes présentent les structs de valeurs qui prennent en charge les nouvelles méthodes d’assistance et les nouveaux constructeurs. Si vous avez déjà écrit du code qui utilise des listes d’initialisation de struct, modifiez-le pour utiliser les constructeurs qui viennent d’être ajoutés.  
  
 **Windows::Foundation**  
  
-   Point  
  
-   Rect  
  
-   Size  
  
 **Windows::UI**  
  
-   Color  
  
 **Windows::UI::Xaml**  
  
-   CornerRadius  
  
-   Duration  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::Xaml::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   Matrix  
  
 **Windows::UI::Xaml::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## <a name="mapping-the-clr-to-ccx"></a>Mappage du CLR pour C++ / c++ / CX  
 Lorsque les compilateurs Visual C++ ou c# lisent un fichier .winmd, ils mappent automatiquement certains types dans le fichier de métadonnées approprié C + c++ / CX ou CLR types. Par exemple, dans le CLR, le IVector\<T > interface est mappée à IList\<T >. Mais en C / c++ / CX, le IVector\<T > interface n’est pas mappée à un autre type.  
  
 IReference\<T > dans le Windows Runtime est mappée à Nullable\<T > dans .NET.  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité avec d’autres langages](../cppcx/interoperating-with-other-languages-c-cx.md)