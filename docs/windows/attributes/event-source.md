---
title: event_source (attribut COM C++)
description: Découvrez comment utiliser l’attribut com de l’extension Microsoft C++ `event_source` .
ms.date: 11/20/2020
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.openlocfilehash: 3cdfaaa86f8fc36bf0dc90d7961077546362a662
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483267"
---
# <a name="event_source-attribute"></a>Attribut `event_source`

Crée une source d'événement.

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="syntax"></a>Syntaxe

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Paramètres

*`type`*\
Une énumération de l’une des valeurs suivantes :

- `native` pour le code C/C++ non managé (par défaut pour les classes non managées).

- `com` pour le code COM. Utilisez `coclass` When *`type`* = `com` . Cette valeur nécessite que vous incluiez les fichiers d’en-tête suivants :

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`optimize`*\
Quand le *type* est `native` , vous pouvez spécifier `optimize=size` , pour indiquer qu’il y a 4 octets de stockage (minimum) pour tous les événements dans une classe ou `optimize=speed` (valeur par défaut) pour indiquer qu’il y a 4 * (nombre d’événements) octets de stockage.

*`decorate`*\
Quand le *type* est `native` , vous pouvez spécifier `decorate=false` , pour indiquer que le nom développé dans le fichier fusionné ( *`.mrg`* ) ne doit pas inclure le nom de la classe englobante. [`/Fx`](../../build/reference/fx-merge-injected-code.md) vous permet de générer des *`.mrg`* fichiers. `decorate=false`, qui est la valeur par défaut, génère des noms de types qualifiés complets dans le fichier fusionné.

## <a name="remarks"></a>Notes

L' **`event_source`** attribut C++ spécifie que la classe ou la structure à laquelle il est appliqué sera une source d’événement.

**`event_source`** est utilisé conjointement avec l' [`event_receiver`](event-receiver.md) attribut et le [`__event`](../../cpp/event.md) mot clé. Utilisez `event_receiver` pour créer des récepteurs d’événements. Utilisez **`__event`** sur les méthodes dans la source d’événements pour spécifier ces méthodes en tant qu’événements.

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|--|--|
| **S’applique à** | **`class`**, **`struct`** |
| **Renouvelable** | Non |
| **Attributs requis** | **`coclass`** à `type`=`com` |
| **Attributs non valides** | None |

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)\
[`event_receiver`](event-receiver.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[Attributs de classe](class-attributes.md)
