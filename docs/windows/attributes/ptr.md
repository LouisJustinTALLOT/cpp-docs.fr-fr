---
title: PTR (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: 2c712a2d9c85e0fe8fd8c4dbad5c7f48812ab1a2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030126"
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
[Attributs d'interface](interface-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)