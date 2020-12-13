---
description: 'En savoir plus sur : ne pouvant pas être exploré'
title: ne pouvant pas être exploré (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonbrowsable
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
ms.openlocfilehash: 943458ff989a3f00d2ce33a4f5681a8bd29a76ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329763"
---
# <a name="nonbrowsable"></a>nonbrowsable

Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.

## <a name="syntax"></a>Syntaxe

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>Notes

L’attribut C++ ne pouvant être **exploré** a les mêmes fonctionnalités que l’attribut MIDL ne pouvant être [exploré](/windows/win32/Midl/nonbrowsable) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_nonbrowsable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, helpstring("help string"), helpstringcontext(1),
uuid="11111111-1111-1111-1111-111111111111"]
__interface IMyI
{
   [nonbrowsable] HRESULT xx();
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
