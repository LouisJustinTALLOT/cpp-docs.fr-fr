---
title: usesgetlasterror | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7921ff48adf2f987844557f9af3be5adcd6736de
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602760"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Indique à l’appelant que s’il existe une erreur lors de l’appel de cette fonction, puis l’appelant peut ensuite appeler `GetLastError` pour récupérer le code d’erreur.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Notes

Le **usesgetlasterror** attribut C++ a les mêmes fonctionnalités que le [usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) attribut MIDL.

## <a name="example"></a>Exemple

Consultez le [idl_module](../windows/idl-module.md) exemple pour obtenir un exemple montrant comment utiliser **usesgetlasterror**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**module** attribut|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  