---
title: Double (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dual
dev_langs:
- C++
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 228349c878e3bef262b5d09790c315e1d8b9e28b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790709"
---
# <a name="dual"></a>dual

Place une interface dans le fichier .idl comme une interface double.

## <a name="syntax"></a>Syntaxe

```cpp
[dual]
```

## <a name="remarks"></a>Notes

Lorsque le **double** attribut C++ précède une interface, il fait en sorte d’être placées dans le bloc de bibliothèque dans le fichier .idl généré.

## <a name="example"></a>Exemple

Le code suivant est un bloc d’attributs qui utilise **double** avant une définition d’interface :

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([in] long nSize); 
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|`dispinterface`|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)<br/>
[custom](custom-cpp.md)<br/>
[dispinterface](dispinterface.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)  