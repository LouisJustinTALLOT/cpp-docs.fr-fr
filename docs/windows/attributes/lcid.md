---
description: 'En savoir plus sur : LCID'
title: LCID (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 2af34574539372a07daadc48874316b0b268f317
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329856"
---
# <a name="lcid"></a>lcid

Vous permet de passer un identificateur de paramètres régionaux à une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
[lcid]
```

## <a name="remarks"></a>Notes

L’attribut C++ **LCID** implémente les fonctionnalités de l’attribut MIDL [LCID](/windows/win32/Midl/lcid) . Si vous souhaitez implémenter des paramètres régionaux pour un bloc de bibliothèque, utilisez le paramètre **LCID =** `lcid` pour l’attribut de [module](module-cpp.md) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)
