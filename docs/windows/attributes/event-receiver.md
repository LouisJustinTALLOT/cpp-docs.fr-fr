---
title: event_receiver (attribut COM C++)
description: Découvrez comment utiliser l’attribut com de l’extension Microsoft C++ `event_receiver` .
ms.date: 11/20/2020
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.openlocfilehash: 8ed6ef6113d72a9565b275dff4e035dc56f11e82
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483280"
---
# <a name="event_receiver-attribute"></a>Attribut `event_receiver`

Crée un récepteur d'événements (récepteur).

> [!NOTE]
> Les attributs d’événement en C++ natif sont incompatibles avec le C++ standard. Elles ne se compilent pas lorsque vous spécifiez le [`/permissive-`](../../build/reference/permissive-standards-conformance.md) mode de conformité.

## <a name="syntax"></a>Syntaxe

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Paramètres

*`type`*\
Une énumération de l’une des valeurs suivantes :

- `native` pour le code C/C++ non managé (par défaut pour les classes natives).

- `com` pour le code COM. Cette valeur nécessite que vous incluiez les fichiers d’en-tête suivants :

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*`layout_dependent`*\
Spécifiez *`layout_dependent`* uniquement si `type` = **com**. *`layout_dependent`* est une valeur booléenne :

- **`true`** signifie que la signature des délégués dans le récepteur d’événements doit correspondre exactement à celles auxquelles elles sont raccordées dans la source de l’événement. Les noms des gestionnaires de récepteur d’événements doivent correspondre aux noms spécifiés dans l’interface de source d’événement appropriée. Utilisez `coclass` lorsque *`layout_dependent`* est **`true`** . C’est un peu plus efficace à spécifier **`true`** .

- **`false`** (valeur par défaut) signifie que la Convention d’appel et la classe de stockage ( `virtual` , `static` , etc.) ne doivent pas nécessairement correspondre à la méthode d’événement et aux gestionnaires. Les noms des gestionnaires n’ont pas non plus besoin de correspondre aux noms des méthodes de l’interface source de l’événement.

## <a name="remarks"></a>Notes

L' **`event_receiver`** attribut C++ spécifie que la classe ou la structure à laquelle il est appliqué sera un récepteur d’événements, à l’aide du modèle d’événement unifié Microsoft C++.

**`event_receiver`** est utilisé avec l' [`event_source`](event-source.md) attribut et les [`__hook`](../../cpp/hook.md) [`__unhook`](../../cpp/unhook.md) Mots clés et. Utilisez `event_source` pour créer des sources d’événements. Utilisez **`__hook`** dans les méthodes d’un récepteur d’événements pour associer des méthodes de récepteur d’événements (« Hook ») aux événements d’une source d’événement. Utilisez **`__unhook`** pour les dissocier.

*`layout_dependent`* est spécifié uniquement pour les récepteurs d’événements COM ( `type` = **`com`** ). La valeur par défaut de *`layout_dependent`* est **`false`** .

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|--|--|
| **S’applique à** | **`class`**, **`struct`** |
| **Renouvelable** | Non |
| **Attributs requis** | `coclass` à *`layout_dependent`*=**`true`** |
| **Attributs non valides** | None |

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)\
[`event_source`](event-source.md)\
[`__event`](../../cpp/event.md)\
[`__hook`](../../cpp/hook.md)\
[`__unhook`](../../cpp/unhook.md)\
[Attributs de classe](class-attributes.md)
