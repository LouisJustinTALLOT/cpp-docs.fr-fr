---
title: entryC++ (attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 71abf4f183255fa137b43ac9cabd88d15c3fc85d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490900"
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

L' C++ attribut Entry a les mêmes fonctionnalités que l’attribut MIDL [entry](/windows/win32/Midl/entry) .

## <a name="example"></a>Exemples

Consultez l’exemple pour [idl_module](idl-module.md) pour obtenir un exemple d’utilisation de l' **entrée**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|`idl_module`attribut|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)