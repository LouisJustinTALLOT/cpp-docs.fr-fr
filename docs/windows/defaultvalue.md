---
title: DefaultValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a27120869c464a9009f8d19cf0f84bfde7a02e96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446053"
---
# <a name="defaultvalue"></a>defaultvalue

Permet de spécifier une valeur par défaut pour un paramètre facultatif typé.

## <a name="syntax"></a>Syntaxe

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>Paramètres

*valeur*<br/>
La valeur par défaut pour le paramètre.

## <a name="remarks"></a>Notes

Le **defaultvalue** attribut C++ a les mêmes fonctionnalités que le [defaultvalue](/windows/desktop/Midl/defaultvalue) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant montre une méthode d’interface à l’aide du **defaultvalue** attribut :

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),
   dual, oleautomation,
   helpstring("IFireTabCtrl Interface"),
   helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs de paramètres](../windows/parameter-attributes.md)<br/>
[out](../windows/out-cpp.md)<br/>
[retval](../windows/retval.md)<br/>
[in](../windows/in-cpp.md)<br/>
[pointer_default](../windows/pointer-default.md)<br/>
[unique](../windows/unique-cpp.md)  