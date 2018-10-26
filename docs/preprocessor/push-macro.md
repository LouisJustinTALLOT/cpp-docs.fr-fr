---
title: push_macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6a389289f8849ac6155543299392586dcd389d2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078945"
---
# <a name="pushmacro"></a>push_macro
Enregistre la valeur de la *macro_name* macro en haut de la pile pour cette macro.

## <a name="syntax"></a>Syntaxe

```
#pragma push_macro("
macro_name
")
```

## <a name="remarks"></a>Notes

Vous pouvez récupérer la valeur de *macro_name* avec `pop_macro`.

Consultez [pop_macro](../preprocessor/pop-macro.md) pour obtenir un exemple.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)