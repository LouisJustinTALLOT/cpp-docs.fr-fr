---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: a3e49941271ec294ddb69861d12e3451332770fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633340"
---
# <a name="autoinline"></a>auto_inline
Exclut toutes les fonctions définies dans la plage où **hors** est spécifié ne soit pas considérée comme des candidats pour l’expansion inline automatique.

## <a name="syntax"></a>Syntaxe

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Notes

Pour utiliser le **auto_inline** pragma, placez-le avant et immédiatement après (et non dans) une définition de fonction. Le pragma est appliqué à la première définition de fonction après détection du pragma.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)