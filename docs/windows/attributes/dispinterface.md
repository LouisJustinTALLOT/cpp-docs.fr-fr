---
title: dispinterface (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b02244e0576f99cc0a6940f2ee4a13511cfbe6f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790581"
---
# <a name="dispinterface"></a>dispinterface

Place une interface dans le fichier .idl comme interface de dispatch.

## <a name="syntax"></a>Syntaxe

```cpp
[dispinterface]
```

## <a name="remarks"></a>Notes

Quand l’attribut C++ **dispinterface** précède une interface, il fait en sorte qu’elle soit placée dans le bloc de bibliothèque dans le fichier .idl généré.

Une interface de dispatch dérivent de `IDispatch`, sauf si vous spécifiez une classe de base. Vous devez spécifier un [id](id.md) pour les membres d’une interface de dispatch.

L’exemple d’utilisation [dispinterface](/windows/desktop/Midl/dispinterface) dans la documentation MIDL :

```cpp
dispinterface helloPro
   { interface hello; };
```

n’est pas valide pour l’attribut **dispinterface** .

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour obtenir un exemple montrant comment utiliser **dispinterface**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)  