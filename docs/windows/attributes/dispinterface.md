---
title: dispinterface (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 6fd5010dc20d03c518206d81919e3beafbcaa9a9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038458"
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

L’exemple d’utilisation de [dispinterface](/windows/desktop/Midl/dispinterface) dans la documentation MIDL :

```cpp
dispinterface helloPro
   { interface hello; };
```

n’est pas valide pour l’attribut **dispinterface** .

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser [dispinterface](bindable.md) , consultez l’exemple de **bindable**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[personnalisé](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)