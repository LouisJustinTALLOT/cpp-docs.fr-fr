---
description: 'En savoir plus sur : dispinterface'
title: dispinterface (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: fe39e537ccbc350f3733653a710dfd0f0d817339
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122133"
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

L’exemple d’utilisation de [dispinterface](/windows/win32/Midl/dispinterface) dans la documentation MIDL :

```cpp
dispinterface helloPro
   { interface hello; };
```

n’est pas valide pour l’attribut **dispinterface** .

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser [dispinterface](bindable.md) , consultez l’exemple de **bindable**.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[double](dual.md)<br/>
[propre](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
