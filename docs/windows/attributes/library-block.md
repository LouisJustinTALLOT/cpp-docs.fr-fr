---
title: library_block (C++ attribut COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 219f6a89dd7f80246e0337c2ef3bcad43540b165
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409250"
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

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)