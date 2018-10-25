---
title: inline_depth | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 672ea8c36b794683dca0ab50af0bda75d73f9a68
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081441"
---
# <a name="inlinedepth"></a>inline_depth
Spécifie la profondeur, de recherche de l’heuristique inline telles qu’aucune fonction ne seront incorporée dans le cas à une profondeur (dans le graphique des appels) supérieure à *n*.

## <a name="syntax"></a>Syntaxe

```
#pragma inline_depth( [n] )
```

## <a name="remarks"></a>Notes

Ce pragma contrôle l’incorporation des fonctions marquées [inline](../cpp/inline-functions-cpp.md) et [__inline](../cpp/inline-functions-cpp.md) ou incorporées automatiquement sous le `/Ob2` option.

*n* peut être une valeur comprise entre 0 et 255, 255 signifie une profondeur illimitée dans le graphique des appels, et zéro INHIBANT l’expansion inline.  Lorsque *n* n’est pas spécifié, la valeur par défaut (254) est utilisé.

Le **inline_depth** pragma contrôle le nombre de fois où une série d’appels de fonction peut être développée. Par exemple, avec une profondeur inline égale à quatre, si A appelle B et B appelle C, les trois appels sont développés inline. Toutefois, si l’expansion inline la plus proche est deux, seuls A et B sont développés, et C demeure comme un appel de fonction.

Pour utiliser ce pragma, vous devez définir le `/Ob` option du compilateur sur 1 ou 2. La profondeur définie à l'aide de ce pragma entre en vigueur au premier appel de fonction après le pragma.

La profondeur inline peut être réduite pendant l'expansion, mais pas augmentée. Si la profondeur inline se situe six emplacements et pendant l’expansion le préprocesseur rencontre un **inline_depth** pragma avec une valeur de huit, la profondeur demeure égale à six.

Le **inline_depth** pragma n’a aucun effet sur les fonctions marquées avec `__forceinline`.

> [!NOTE]
> Les fonctions récursives peuvent être substituées inline à une profondeur maximale de 16 appels.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_recursion](../preprocessor/inline-recursion.md)