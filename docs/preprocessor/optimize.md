---
title: optimize
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 9f5240fc59f59a71ddb3d18b67fadf3463a0d1ea
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035398"
---
# <a name="optimize"></a>optimize

Spécifie les optimisations à effectuer sur une base fonction par fonction.

## <a name="syntax"></a>Syntaxe

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>Notes

Le **optimiser** pragma doit apparaître en dehors d’une fonction et prend effet à la première fonction définie après le pragma. Le *sur* et *hors* arguments activer des options spécifiées dans le *liste d’optimisation* activé ou désactivé.

Le *liste d’optimisation* peut être zéro ou plusieurs des paramètres indiqués dans le tableau suivant.

### <a name="parameters-of-the-optimize-pragma"></a>Paramètres du pragma optimize

|Paramètre(s)|Type d'optimisation|
|--------------------|--------------------------|
|*g*|Active les optimisations globales.|
|*s* ou *t*|Spécifie des séquences courtes ou rapides de code machine.|
|*o*|Génère des pointeurs de frame sur la pile du programme.|

Ce sont les mêmes lettres que celui utilisés avec le [/O](../build/reference/o-options-optimize-code.md) options du compilateur. Par exemple, le pragma suivant équivaut à l'option du compilateur `/Os` :

```
#pragma optimize( "ts", on )
```

À l’aide de la **optimiser** pragma avec la chaîne vide (**» «**) est une forme spéciale de la directive :

Lorsque vous utilisez le *hors* paramètre, il désactive toutes les optimisations, *g*, *s*, *t*, et *y*, off.

Lorsque vous utilisez le *sur* paramètre, il réinitialise les optimisations à celles que vous avez spécifié avec la [/O](../build/reference/o-options-optimize-code.md) option du compilateur.

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)