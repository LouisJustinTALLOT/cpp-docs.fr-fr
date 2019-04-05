---
title: unique (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.unique
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
ms.openlocfilehash: c5d7a2d60dc295a4390f777a9ff3718f41321ddd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038788"
---
# <a name="unique-c"></a>unique (C++)

Spécifie un pointeur unique.

## <a name="syntax"></a>Syntaxe

```cpp
[unique]
```

## <a name="remarks"></a>Notes

Le **unique** attribut C++ a les mêmes fonctionnalités que le [unique](/windows/desktop/Midl/unique) attribut MIDL.

## <a name="example"></a>Exemple

Consultez le [ref](ref-cpp.md) exemple pour un exemple d’utilisation de **unique**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**, **struct**, **union**, paramètre de l’interface, interface (méthode)|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)