---
title: unique (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.unique
dev_langs:
- C++
helpviewer_keywords:
- unique attribute
ms.assetid: abd7ed14-5ae7-44a8-8333-0058e9c92b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc90c58162993cd8d663581e5b19604fcce4c668
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790665"
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

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)  