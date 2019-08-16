---
title: pointer_default (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: c70c372e5f1c3a9c2f620a1fa3505fb9d0436e79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514259"
---
# <a name="pointer_default"></a>pointer_default

Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur qui décrit le type de pointeur: **ptr**, **ref**ou **unique**.

## <a name="remarks"></a>Notes

L’attribut **pointer_default** C++ a les mêmes fonctionnalités que l’attribut MIDL [pointer_default](/windows/win32/Midl/pointer-default) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **pointer_default**, consultez l’exemple correspondant à [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)