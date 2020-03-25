---
title: dispinterface (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 66567b0a1b043136e0a754e3a52bbdd7c463e178
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168237"
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

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
