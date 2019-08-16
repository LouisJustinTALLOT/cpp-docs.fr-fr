---
title: LCID (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 7c737661bb8429e416b515e4e7fcaf54956385d0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514540"
---
# <a name="lcid"></a>lcid

Vous permet de passer un identificateur de paramètres régionaux à une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
[lcid]
```

## <a name="remarks"></a>Notes

L’attribut **LCID** C++ implémente les fonctionnalités de l’attribut MIDL [LCID](/windows/win32/Midl/lcid) . Si vous souhaitez implémenter des paramètres régionaux pour un bloc de bibliothèque, utilisez le paramètre **LCID =** `lcid` pour l’attribut de [module](module-cpp.md) .

## <a name="example"></a>Exemples

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)