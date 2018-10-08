---
title: library_block (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf4bcdd9290817bb77eeb20f1a014bd537d15d8b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790889"
---
# <a name="libraryblock"></a>library_block

Place une construction dans le bloc de bibliothèque IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[library_block]
```

## <a name="remarks"></a>Notes

Lorsque vous placez une construction dans le bloc de bibliothèque, vous assurez qu’il sera passé dans la bibliothèque de types, indépendamment de si elle est référencée. Par défaut, les seules constructions modifiés par le [coclasse](coclass.md), [dispinterface](dispinterface.md), et [idl_module](idl-module.md) attributs sont placés dans le bloc de bibliothèque.

## <a name="example"></a>Exemple

Dans le code suivant, une interface personnalisée est placée dans le bloc de bibliothèque.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)  