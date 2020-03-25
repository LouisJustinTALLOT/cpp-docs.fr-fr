---
title: Plage (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: 380f7c9e15a3682b486217c842f00c944251e631
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214615"
---
# <a name="range-c"></a>range (C++)

Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>Paramètres

*low*<br/>
Valeur de plage inférieure.

*high*<br/>
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

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Méthode d’interface, paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de membre de données](data-member-attributes.md)
