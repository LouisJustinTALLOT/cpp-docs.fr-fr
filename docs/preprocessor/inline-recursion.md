---
title: inline_recursion
ms.date: 11/04/2016
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 80ffabc6ac7c95fd7d9fb4e62bea38c2a04b04f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026910"
---
# <a name="inlinerecursion"></a>inline_recursion
Contrôle l'expansion inline des appels de fonction directe ou mutuellement récursive.

## <a name="syntax"></a>Syntaxe

```
#pragma inline_recursion( [{on | off}] )
```

## <a name="remarks"></a>Notes

Utiliser ce pragma pour contrôler les fonctions marqué comme [inline](../cpp/inline-functions-cpp.md) et [__inline](../cpp/inline-functions-cpp.md) ou des fonctions que le compilateur développe automatiquement sous le `/Ob2` option. Utilisation de ce pragma requiert un [/Ob](../build/reference/ob-inline-function-expansion.md) paramètre d’option du compilateur de 1 ou 2. L’état par défaut **inline_recursion** est désactivé. Ce pragma entre en vigueur au premier appel de fonction après sa détection et n'a aucune incidence sur la définition de la fonction.

Le **inline_recursion** pragma contrôle comment les fonctions récursives sont développées. Si **inline_recursion** est désactivée, et si une fonction inline s’appelle elle-même (directement ou indirectement), la fonction est étendue qu’une seule fois. Si **inline_recursion** est activé, la fonction est développée plusieurs fois jusqu'à ce qu’il atteigne la valeur définie avec la [inline_depth](../preprocessor/inline-depth.md) pragma, la valeur par défaut pour les fonctions récursives qui est définie par le `inline_depth` pragma, ou une capacité limite.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob (Expansion des fonctions Inline)](../build/reference/ob-inline-function-expansion.md)