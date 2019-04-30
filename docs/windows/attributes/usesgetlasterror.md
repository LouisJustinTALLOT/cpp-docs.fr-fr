---
title: usesgetlasterror (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 9f050bbf69edf1ab8327a283299cb5e687ce5380
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407066"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indique à l’appelant que s’il existe une erreur lors de l’appel de cette fonction, puis l’appelant peut ensuite appeler `GetLastError` pour récupérer le code d’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Notes

Le **usesgetlasterror** attribut C++ a les mêmes fonctionnalités que le [usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) attribut MIDL.

## <a name="example"></a>Exemple

Consultez le [idl_module](idl-module.md) exemple pour obtenir un exemple montrant comment utiliser **usesgetlasterror**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**module** attribut|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)