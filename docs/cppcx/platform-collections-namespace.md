---
title: Platform::Collections Namespace | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
dev_langs:
- C++
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d872df7294e33ef47247609af4606da842bb6184
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686545"
---
# <a name="platformcollections-namespace"></a>Platform::Collections (espace de noms)

L’espace de noms Platform::Collections contient le `Map`, `MapView`, `Vector`, et `VectorView` classes. Ces classes sont des implémentations concrètes des interfaces correspondantes qui sont définies dans le [Windows::Foundation](/uwp/api/Windows.Foundation.Collections) espace de noms. Les types de collection concrets ne sont pas portables à travers l'ABI (par exemple, lorsqu'un programme JavaScript ou C# fait appel au composant C++), mais ils sont implicitement convertibles en leurs types d'interface correspondants. Par exemple, si vous implémentez une méthode publique qui remplit et retourne une collection, utilisez [Platform::Collections :: Vector](../cppcx/platform-collections-vector-class.md) pour implémenter la collection en interne et utilisez [Windows::Foundation :: Collections : : IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) comme type de retour. Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md) et [création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Vous pouvez construire un Platform::Collections::Vector à partir d'un [std::vector](../standard-library/vector-class.md) et un [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) à partir d'un [std::map](../standard-library/map-class.md).

En outre, l’espace de noms Platform::Collections prend en charge insert back et itérateurs d’entrée, et `Vector` et `VectorView` itérateurs.

Vous devez inclure (`#include`) l’en-tête collection.h pour utiliser les types dans l’espace de noms Platform::Collections.

## <a name="syntax"></a>Syntaxe

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Membres

Cet espace de noms contient les membres ci-dessous.

|Name|Description|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator, classe](../cppcx/platform-collections-backinsertiterator-class.md)|Représente un itérateur qui insère un élément à la fin d'une collection.|
|[Platform::Collections::InputIterator, classe](../cppcx/platform-collections-inputiterator-class.md)|Représente un itérateur qui insère un élément au début d'une collection.|
|[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)|Représente une collection modifiable de paires clé/valeur accessibles par une clé. Semblable à [std::map](../standard-library/map-class.md).|
|[classe Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)|Représente une collection en lecture seule de paires clé/valeur accessibles par une clé.|
|[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)|Représente une séquence d'éléments modifiable. Semblable à [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator, classe](../cppcx/platform-collections-vectoriterator-class.md)|Représente un itérateur qui parcourt une collection `Vector` .|
|[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)|Représente une séquence d'éléments en lecture seule.|
|[Platform::Collections::VectorViewIterator, classe](../cppcx/platform-collections-vectorviewiterator-class.md)|Représente un itérateur qui parcourt une collection `VectorView` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Configuration requise

**Métadonnées :** platform.winmd

**Espace de noms :** Platform::Collections

**Option du compilateur :** /ZW

## <a name="see-also"></a>Voir aussi

[Plateforme Namespace](../cppcx/platform-namespace-c-cx.md)  
