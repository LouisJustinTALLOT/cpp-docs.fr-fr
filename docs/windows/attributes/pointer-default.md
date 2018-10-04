---
title: pointer_default (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e8ddf566082bfded1f20a2bfe04e7cef0b5dc14
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790585"
---
# <a name="pointerdefault"></a>pointer_default

Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui s’affichent dans les listes de paramètres.

## <a name="syntax"></a>Syntaxe

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Paramètres

*valeur*<br/>
Une valeur qui décrit le type de pointeur : **ptr**, **ref**, ou **unique**.

## <a name="remarks"></a>Notes

Le **pointer_default** attribut C++ a les mêmes fonctionnalités que le [pointer_default](/windows/desktop/Midl/pointer-default) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](defaultvalue.md) pour un exemple d’utilisation de **pointer_default**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)  