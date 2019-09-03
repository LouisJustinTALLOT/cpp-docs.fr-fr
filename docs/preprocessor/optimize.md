---
title: optimize, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220516"
---
# <a name="optimize-pragma"></a>optimize, pragma

Spécifie des optimisations fonction par fonction.

## <a name="syntax"></a>Syntaxe

> **#pragma optimize ("** [ *Optimization-List* ] **",** { **on** | **off** } **)**

## <a name="remarks"></a>Notes

Le pragma **optimize** doit apparaître en dehors d’une fonction. Elle prend effet à la première fonction définie après l’affichage du pragma. Les arguments **on** et **off** activent ou désactivent les options spécifiées dans la *liste d’optimisation* .

La *liste* d’optimisations peut être égale à zéro ou plusieurs des paramètres indiqués dans le tableau suivant.

### <a name="parameters-of-the-optimize-pragma"></a>Paramètres du pragma optimize

| Paramètre(s) | Type d'optimisation |
|--------------------|--------------------------|
| **g** | Active les optimisations globales. |
| **s** ou **t** | Spécifie des séquences courtes ou rapides de code machine. |
| **y** | Génère des pointeurs de frame sur la pile du programme. |

Ces paramètres sont les mêmes que ceux utilisés avec les options du compilateur [/o](../build/reference/o-options-optimize-code.md) . Par exemple, le pragma suivant équivaut à l'option du compilateur `/Os` :

```cpp
#pragma optimize( "s", on )
```

L’utilisation du pragma **optimize** avec la chaîne vide ( **""** ) est une forme spéciale de la directive:

Quand vous utilisez le paramètre **off** , il désactive toutes les optimisations, **g**, **s**, **t**et **y**, OFF.

Quand vous utilisez le paramètre **on** , il réinitialise les optimisations à celles que vous avez spécifiées à l’aide de l’option du compilateur [/o](../build/reference/o-options-optimize-code.md) .

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
