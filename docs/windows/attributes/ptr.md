---
title: PTR (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: 7ed08403f32e5e4609266975c5c479a7b758fe89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506208"
---
# <a name="ptr"></a>ptr

Désigne un pointeur comme un pointeur complet.

## <a name="syntax"></a>Syntaxe

```cpp
[ptr]
```

## <a name="remarks"></a>Notes

Le **ptr** attribut C++ a les mêmes fonctionnalités que le [ptr](/windows/desktop/Midl/ptr) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](defaultvalue.md) pour un exemple d’utilisation de **ptr**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, la méthode d’interface, **(typedef)**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)