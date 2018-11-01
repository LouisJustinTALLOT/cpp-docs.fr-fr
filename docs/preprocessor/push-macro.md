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
ms.openlocfilehash: 9b866fd5907faf46872665bbcaef97f2352efea9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535679"
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