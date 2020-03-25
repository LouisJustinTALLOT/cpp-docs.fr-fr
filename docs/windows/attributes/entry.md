---
title: entryC++ (attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167093"
---
# <a name="entry"></a>entry

Spécifie une fonction ou une constante exportée dans un module en identifiant le point d’entrée dans la DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Paramètres

*id*<br/>
ID du point d’entrée.

## <a name="remarks"></a>Notes

L’attribut **entry** C++ a les mêmes fonctionnalités que l’attribut MIDL [entry](/windows/win32/Midl/entry) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **entrée**, consultez l’exemple de [idl_module](idl-module.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Attribut `idl_module`|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)
