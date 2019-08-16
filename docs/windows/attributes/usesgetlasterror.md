---
title: usesgetlasterror (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: b14316bd929f4b41b13a76c41e94b31b7534e9d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513893"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indique à l’appelant qu’en cas d’erreur lors de l’appel de cette fonction, l’appelant peut `GetLastError` alors appeler pour récupérer le code d’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Notes

L’attribut **usesgetlasterror** C++ a les mêmes fonctionnalités que l’attribut MIDL [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) .

## <a name="example"></a>Exemples

Pour obtenir un exemple d’utilisation de **usesgetlasterror**, consultez l’exemple [idl_module](idl-module.md) .

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|attribut de **module**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)