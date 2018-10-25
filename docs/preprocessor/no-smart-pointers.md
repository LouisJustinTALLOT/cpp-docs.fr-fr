---
title: no_smart_pointers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 233e302d4035801e7d8871754d8ecfcfee54cf1a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060909"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Spécifique à C++**

Supprime la création des pointeurs intelligents pour toutes les interfaces dans la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```
no_smart_pointers
```

## <a name="remarks"></a>Notes

Par défaut, lorsque vous utilisez `#import`, vous obtenez une déclaration de pointeur intelligent pour toutes les interfaces dans la bibliothèque de types. Ces pointeurs intelligents sont de type [_com_ptr_t, classe](../cpp/com-ptr-t-class.md).

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)