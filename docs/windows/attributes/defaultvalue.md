---
description: 'En savoir plus sur : DefaultValue'
title: DefaultValue (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvalue
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
ms.openlocfilehash: 907c736861d39064103af28917f35a97c0c7b1e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122159"
---
# <a name="defaultvalue"></a>defaultvalue

Autorise la spécification d’une valeur par défaut pour un paramètre facultatif typé.

## <a name="syntax"></a>Syntaxe

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur par défaut du paramètre.

## <a name="remarks"></a>Notes

L’attribut C++ **DefaultValue** a les mêmes fonctionnalités que l’attribut MIDL [DefaultValue](/windows/win32/Midl/defaultvalue) .

## <a name="example"></a>Exemple

Le code suivant illustre une méthode d’interface à l’aide de l’attribut **DefaultValue** :

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"), dual, oleautomation, helpstring("IFireTabCtrl Interface"), helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",    version="1.0", helpstring="ATLFire 1.0 Type Library") ];
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
[Attributs de paramètre](parameter-attributes.md)<br/>
[à](out-cpp.md)<br/>
[retval](retval.md)<br/>
[in](in-cpp.md)<br/>
[pointer_default](pointer-default.md)<br/>
[unique](unique-cpp.md)
