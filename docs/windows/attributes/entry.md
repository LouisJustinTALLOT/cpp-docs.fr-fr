---
description: 'En savoir plus sur : entrée'
title: entry (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: fbceea4c23d730ceba780ce68398a9d78fa9c33b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259225"
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

L’attribut C++ **entry** a les mêmes fonctionnalités que l’attribut MIDL [entry](/windows/win32/Midl/entry) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de l' **entrée**, consultez l’exemple de [idl_module](idl-module.md) .

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Attribut `idl_module`|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)
