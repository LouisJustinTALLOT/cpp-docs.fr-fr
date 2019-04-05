---
title: iid_is (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: b91fb7937bb0e20f2500eace9695bc0ddba21b26
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038555"
---
# <a name="iidis"></a>iid_is

Spécifie l’IID de l’interface COM vers laquelle pointé un pointeur d’interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Paramètres

*expression*<br/>
Une expression de langage C qui spécifie un IID d’une interface COM vers laquelle pointe un pointeur d’interface.

## <a name="remarks"></a>Notes

Le **iid_is** attribut C++ a les mêmes fonctionnalités que le [iid_is](/windows/desktop/Midl/iid-is) attribut MIDL.

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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, membre de données|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)