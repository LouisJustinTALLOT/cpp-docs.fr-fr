---
description: 'En savoir plus sur : library_block'
title: library_block (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 486c40fa8641e74b6e3bc72bc7f980e3ee1216e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329821"
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

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs du compilateur](compiler-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
