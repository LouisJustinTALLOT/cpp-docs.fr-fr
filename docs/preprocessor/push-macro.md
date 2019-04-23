---
title: push_macro
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.push_macro
- push_macro_CPP
helpviewer_keywords:
- pragmas, push_macro
- push_macro pragma
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
ms.openlocfilehash: 5602dd91b7d017c49a122524e469100b0ec6debf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029740"
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