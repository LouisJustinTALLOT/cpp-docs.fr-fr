---
title: boucle
ms.date: 10/18/2018
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: a1640881d98073381a941478f4b78177a95698d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411329"
---
# <a name="loop"></a>boucle

Contrôle la façon dont le code de la boucle doit être considéré par le paralléliseur automatique et/ou exclut une boucle de la considération par le vectoriseur automatique.

## <a name="syntax"></a>Syntaxe

```
#pragma loop( hint_parallel(n) )
#pragma loop( no_vector )
#pragma loop( ivdep )
```

### <a name="parameters"></a>Paramètres

*hint_parallel(n)*<br/>
Indique au compilateur que cette boucle doit être parallélisée sur *n* threads, où *n* est un littéral entier positif ou zéro. Si *n* est égal à zéro, le nombre maximal de threads est utilisé au moment de l’exécution. Il s'agit d'un indicateur pour le compilateur, et non d'une commande, et il n'existe aucune garantie que la boucle soit parallélisée. Si la boucle présente des dépendances de données ou des problèmes structurels, par exemple si la boucle stocke dans un élément scalaire utilisé au-delà du corps de la boucle, la boucle ne sera pas parallélisée.

Le compilateur ignore cette option, sauf si le [/Qpar](../build/reference/qpar-auto-parallelizer.md) commutateur de compilateur est spécifié.

*no_vector*<br/>
Par défaut, le vectoriseur automatique est activé et tente de vectoriser toutes les boucles considérées comme en tirant parti. Spécifiez ce pragma pour désactiver le vectoriseur automatique de la boucle qui le suit.

*ivdep*<br/>
Indique au compilateur d'ignorer les dépendances vectorielles pour cette boucle. Utilisez-le conjointement avec *hint_parallel*.

## <a name="remarks"></a>Notes

Pour utiliser le **boucle** pragma, placez-le immédiatement avant — pas dans : une définition de la boucle. Le pragma prend effet pour la portée de la boucle qui le suit. Vous pouvez appliquer plusieurs pragmas à une boucle, dans n'importe quel ordre, mais chacun doit être indiqué dans une instruction pragma distincte.

## <a name="see-also"></a>Voir aussi

[Parallélisation et vectorisation automatiques](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)