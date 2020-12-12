---
description: 'En savoir plus sur : REF (C++)'
title: Ref (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ref
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
ms.openlocfilehash: 2ddfafee97f0b8b6a8c35fdff8664335ba6aa10d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114921"
---
# <a name="ref-c"></a>ref (C++)

Identifie un pointeur de référence.

## <a name="syntax"></a>Syntaxe

```cpp
[ref]
```

## <a name="remarks"></a>Notes

L’attribut **ref** C++ a les mêmes fonctionnalités que l’attribut MIDL [ref](/windows/win32/Midl/ref) .

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de l’attribut **ref** :

```cpp
// cpp_attr_ref_ref.cpp
// compile with: /LD
#include <windows.h>
[module(name="ATLFIRELib")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**`typedef`**, paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)
