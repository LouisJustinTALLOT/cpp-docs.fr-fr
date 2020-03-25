---
title: library_block (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 405cc1cd5af7dcd689e833764f3da2fdc6d5f703
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214771"
---
# <a name="library_block"></a>library_block

Place une construction dans le bloc de bibliothèque IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[library_block]
```

## <a name="remarks"></a>Notes

Lorsque vous placez une construction dans le bloc de bibliothèque, vous vous assurez qu’elle sera passée dans la bibliothèque de types, qu’elle soit référencée ou non. Par défaut, seules les constructions modifiées par les attributs [coclass](coclass.md), [dispinterface](dispinterface.md)et [idl_module](idl-module.md) sont placées dans le bloc de bibliothèque.

## <a name="example"></a>Exemple

Dans le code suivant, une interface personnalisée est placée à l’intérieur du bloc de bibliothèque.

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

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
