---
title: rename_search_namespace | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_search_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_search_namespace attribute
ms.assetid: 47c9d7fd-59dc-4c62-87a1-9011a0040167
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cc95851c4aa7127e690ec013b9d06d57f2730d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808886"
---
# <a name="renamesearchnamespace"></a>rename_search_namespace

**Spécifique à C++**

A les mêmes fonctionnalités que le [rename_namespace](../preprocessor/rename-namespace.md) d’attribut, mais est utilisée sur les bibliothèques de types que vous utilisez le `#import` directive avec la [auto_search](../preprocessor/auto-search.md) attribut.

## <a name="syntax"></a>Syntaxe

```
rename_search_namespace("NewName")
```

### <a name="parameters"></a>Paramètres

*NewName*<br/>
Nom du nouvel espace de noms.

## <a name="remarks"></a>Notes

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)