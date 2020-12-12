---
description: 'En savoir plus sur : pragma inline_depth'
title: inline_depth, pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 10ac7f5543108018eb7b51e8916dfed149363899
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236397"
---
# <a name="inline_depth-pragma"></a>inline_depth, pragma

Spécifie la profondeur de recherche heuristique Inline. Les fonctions d’une profondeur dans le graphique des appels supérieures à la valeur spécifiée ne sont pas Inline.

## <a name="syntax"></a>Syntaxe

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>Notes

Ce pragma contrôle l’incorporation des fonctions marquées [inline](../cpp/inline-functions-cpp.md) et [__inline](../cpp/inline-functions-cpp.md), ou Inline automatiquement sous l' `/Ob` option.

*n* peut être une valeur comprise entre 0 et 255, où 255 signifie une profondeur illimitée dans le graphique des appels. La valeur 0 empêche l’expansion Inline. Lorsque *n* n’est pas spécifié, la valeur par défaut 254 est utilisée.

Le pragma **inline_depth** contrôle le nombre de fois qu’une série d’appels de fonction peut être développée. Par exemple, supposons que la profondeur Inline est 4. Si A appelle B et que B appelle ensuite C, les trois appels sont développés Inline. Toutefois, si l’expansion de profondeur Inline la plus proche est 2, seuls A et B sont développés, et C reste un appel de fonction.

Pour utiliser ce pragma, vous devez définir l' `/Ob` option de compilateur sur une valeur supérieure ou égale à 1. La profondeur définie à l'aide de ce pragma entre en vigueur au premier appel de fonction après le pragma.

La profondeur incluse peut être réduite pendant l’expansion, mais elle n’est pas augmentée. Si la profondeur incluse est 6, et Pendant l’expansion, le préprocesseur rencontre un **inline_depth** pragma avec une valeur de 8, la profondeur reste 6.

Le pragma **inline_depth** n’a aucun effet sur les fonctions marquées avec **`__forceinline`** .

> [!NOTE]
> Les fonctions récursives peuvent être substituées inline à une profondeur maximale de 16 appels.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
