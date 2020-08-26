---
title: event_receiver (attribut COM C++)
ms.date: 10/02/2018
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
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 7280729a9ae3a054468e1f11bdcc4a563b32effe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845287"
---
# <a name="event_receiver"></a>event_receiver

Crée un récepteur d'événements (récepteur).

## <a name="syntax"></a>Syntaxe

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Une énumération de l’une des valeurs suivantes :

- `native` pour le code C/C++ non managé (par défaut pour les classes natives).

- `com` pour le code COM. Cette valeur nécessite que vous incluiez les fichiers d’en-tête suivants :

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Spécifiez *layout_dependent* uniquement si `type` = **com**. *layout_dependent* est une valeur booléenne :

- **`true`** signifie que la signature des délégués dans le récepteur d’événements doit correspondre exactement à ceux auxquels ils sont raccordés dans la source de l’événement. Les noms des gestionnaires de récepteur d’événements doivent correspondre aux noms spécifiés dans l’interface de source d’événement appropriée. Vous devez utiliser `coclass` lorsque *layout_dependent* est **`true`** . Il est légèrement plus efficace de spécifier **`true`** .

- **`false`** (par défaut) signifie que la Convention d’appel et la classe de stockage (virtuelles, statiques et autres) ne doivent pas nécessairement correspondre à la méthode d’événement et aux gestionnaires ; les noms des gestionnaires ne doivent pas non plus correspondre aux noms des méthodes de l’interface source de l’événement.

## <a name="remarks"></a>Notes

L’attribut **event_receiver** C++ spécifie que la classe ou la structure à laquelle il est appliqué est un récepteur d’événements, à l’aide du modèle d’événement unifié Visual C++.

**event_receiver** est utilisé avec l’attribut [event_source](event-source.md) et les mots clés [__hook](../../cpp/hook.md) et [__unhook](../../cpp/unhook.md) . Utilisez `event_source` pour créer des sources d’événements. Utilisez **`__hook`** dans les méthodes d’un récepteur d’événements pour associer des méthodes de récepteur d’événements (« Hook ») aux événements d’une source d’événement. Utilisez **`__unhook`** pour les dissocier.

*layout_dependent* est spécifié uniquement pour les récepteurs d’événements COM ( `type` = **com**). La valeur par défaut de *layout_dependent* est **`false`** .

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`class`**, **`struct`**|
|**Repeatable Read**|Non|
|**Attributs requis**|`coclass` quand *layout_dependent*=**`true`**|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Attributs de classe](class-attributes.md)
