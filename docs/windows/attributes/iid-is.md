---
description: 'En savoir plus sur : iid_is'
title: iid_is (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 9de6d636fbb189ece9aedec95cb9460c2ccbb5a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183098"
---
# <a name="iid_is"></a>iid_is

Spécifie l’IID de l’interface COM vers laquelle pointe un pointeur d’interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Expression de langage C qui spécifie un IID d’une interface COM vers laquelle pointe un pointeur d’interface.

## <a name="remarks"></a>Notes

L’attribut C++ **iid_is** a les mêmes fonctionnalités que l’attribut MIDL [iid_is](/windows/win32/Midl/iid-is) .

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface, membre de données|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)
