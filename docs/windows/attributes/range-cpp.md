---
title: Range (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 8ed0ba2c53992dd19d1c4491f8085e955146224c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839476"
---
# <a name="range-c"></a>range (C++)

Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Paramètres

*entrée*<br/>
Valeur de plage inférieure.

*rapide*<br/>
Valeur de plage supérieure.

## <a name="remarks"></a>Notes

L’attribut **Range** C++ a les mêmes fonctionnalités que l’attribut MIDL [Range](/windows/win32/Midl/range) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface, paramètre d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)
