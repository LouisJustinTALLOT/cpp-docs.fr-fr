---
title: event_source (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 750e51264f12d1c8961ced4e8b606ea5d040d8c9
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790680"
---
# <a name="eventsource"></a>event_source

Crée une source d'événement.

## <a name="syntax"></a>Syntaxe

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Une énumération de l’une des valeurs suivantes :

- `native` pour le code C/C++ non managé (par défaut pour les classes non managées).

- `com` pour le code COM. Vous devez utiliser `coclass` quand `type`=`com`. Cette valeur nécessite que vous incluiez les fichiers d’en-tête suivants :

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Lorsque *type* est `native`, vous pouvez spécifier `optimize=size`, pour indiquer qu’il y a 4 octets de stockage (minimum) pour tous les événements dans une classe ou `optimize=speed` (la valeur par défaut) pour indiquer qu’il y a 4 * (nombre d’événements) octets de stockage.

*décorer*<br/>
Lorsque *type* est `native`, vous pouvez spécifier `decorate=false`, pour indiquer que le nom développé dans le fichier fusionné (.mrg) ne doit pas inclure le nom de la classe englobante. [/FX](../../build/reference/fx-merge-injected-code.md) vous permet de générer des fichiers .mrg. `decorate=false`, qui est la valeur par défaut, génère dans les noms de types qualifiés complets dans le fichier fusionné.

## <a name="remarks"></a>Notes

L’attribut C++ **event_source** indique que la classe ou structure à laquelle il est appliqué est une source d’événements.

**event_source** est utilisé conjointement avec le [event_receiver](event-receiver.md) attribut et la [__event](../../cpp/event.md) mot clé. Utilisez `event_receiver` pour créer des récepteurs d’événements. Utilisez **__event** sur les méthodes dans la source d’événements pour spécifier ces méthodes en tant qu’événements.

> [!NOTE]
> Une classe ou structure modélisée ne peut pas contenir d'événements.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclasse** lorsque `type`=`com`|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Attributs de classe](class-attributes.md)  