---
title: Platform::Collections (espace de noms)
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: ab6b78f1b88c586a11276d36387fb42ea6ee667f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032419"
---
# <a name="platformcollections-namespace"></a>Platform::Collections (espace de noms)

La plate-forme::Collections `Map`namespace `Vector`contient `VectorView` le , `MapView`, , et les classes. Ces classes sont des implémentations concrètes des interfaces correspondantes qui sont définies dans l’espace de noms [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) . Les types de collection concrets ne sont pas portables à travers l'ABI (par exemple, lorsqu'un programme JavaScript ou C# fait appel au composant C++), mais ils sont implicitement convertibles en leurs types d'interface correspondants. Par exemple, si vous implémentez une méthode publique qui remplit et retourne une collection, utilisez [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) pour implémenter la collection en interne et utilisez [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) comme type de retour. Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md) et [Création de composants Windows Runtime dans C .](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)

Vous pouvez construire un Platform::Collections::Vector à partir d'un [std::vector](../standard-library/vector-class.md) et un [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) à partir d'un [std::map](../standard-library/map-class.md).

En outre, la plate-forme::Collections namespace fournit un support `Vector` `VectorView` pour les itérateurs d’insertion et d’entrée de dos, et les itérateurs.

Vous devez`#include`inclure ( ) l’en-tête collection.h pour utiliser les types dans la plate-forme::Collections namespace.

## <a name="syntax"></a>Syntaxe

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Membres

Cet espace de noms contient les membres ci-dessous.

|Nom|Description|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator, classe](../cppcx/platform-collections-backinsertiterator-class.md)|Représente un itérateur qui insère un élément à la fin d'une collection.|
|[Platform::Collections::InputIterator, classe](../cppcx/platform-collections-inputiterator-class.md)|Représente un itérateur qui insère un élément au début d'une collection.|
|[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)|Représente une collection modifiable de paires clé/valeur accessibles par une clé. Semblable à [std::map](../standard-library/map-class.md).|
|[Platform::Collections::MapView, classe](../cppcx/platform-collections-mapview-class.md)|Représente une collection en lecture seule de paires clé/valeur accessibles par une clé.|
|[Platform::Collections::Vector, classe](../cppcx/platform-collections-vector-class.md)|Représente une séquence d'éléments modifiable. Semblable à [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator, classe](../cppcx/platform-collections-vectoriterator-class.md)|Représente un itérateur qui parcourt une collection `Vector` .|
|[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)|Représente une séquence d'éléments en lecture seule.|
|[Platform::Collections::VectorViewIterator, classe](../cppcx/platform-collections-vectorviewiterator-class.md)|Représente un itérateur qui parcourt une collection `VectorView` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Spécifications

**Métadonnées:** platform.winmd

**Espace de noms :** Platform::Collections

**Option Compilateur:** /ZW

## <a name="see-also"></a>Voir aussi

[Espace nom de la plate-forme](../cppcx/platform-namespace-c-cx.md)
