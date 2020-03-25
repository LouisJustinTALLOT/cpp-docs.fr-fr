---
title: usesgetlasterror (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: f58929db01a1710e811a973c0559ad29b242b4eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166131"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indique à l’appelant qu’en cas d’erreur lors de l’appel de cette fonction, l’appelant peut alors appeler `GetLastError` pour récupérer le code d’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Notes

L’attribut **usesgetlasterror** C++ a les mêmes fonctionnalités que l’attribut MIDL [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **usesgetlasterror**, consultez l’exemple de [idl_module](idl-module.md) .

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|attribut de **module**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)
