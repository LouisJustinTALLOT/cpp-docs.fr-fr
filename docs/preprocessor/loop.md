---
description: 'En savoir plus sur : pragma de boucle'
title: loop, pragma
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: b54d62a6c9a29a4688453992ad9647d9bc21afd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167459"
---
# <a name="loop-pragma"></a>loop, pragma

Contrôle la façon dont le code de boucle doit être pris en compte par le paralléliseur automatique, ou exclut une boucle du vectoriseur automatique.

## <a name="syntax"></a>Syntaxe

> **boucle de #pragma (hint_parallel (** *n* **))**\
> **boucle de #pragma (no_vector)**\
> **boucle de #pragma (ivdep)**

### <a name="parameters"></a>Paramètres

**hint_parallel (** *n* **)**\
Indication au compilateur que cette boucle doit être parallélisée sur *n* threads, où *n* est un littéral entier positif ou zéro. Si *n* est égal à zéro, le nombre maximal de threads est utilisé au moment de l’exécution. Il s’agit d’un indicateur pour le compilateur, et non d’une commande. Il n’y a aucune garantie que la boucle sera parallélisée. Si la boucle a des dépendances de données ou des problèmes structurels, elle ne sera pas parallélisée. Par exemple, elle n’est pas parallélisée si elle est stockée sur une valeur scalaire qui est utilisée au-delà du corps de la boucle.

Le compilateur ignore cette option, sauf si le commutateur du compilateur [/QPAR](../build/reference/qpar-auto-parallelizer.md) est spécifié.

**no_vector**\
Par défaut, le vectoriseur automatique tente de vectoriser toutes les boucles qu’il évalue peut en tirer parti. Spécifiez ce pragma pour désactiver la vectoriseur automatique pour la boucle qui suit.

**ivdep**\
Indicateur permettant au compilateur d’ignorer les dépendances vectorielles pour cette boucle.

## <a name="remarks"></a>Notes

Pour utiliser le pragma de **boucle** , placez-le immédiatement avant, et non dans, une définition de boucle. Le pragma prend effet pour la portée de la boucle qui le suit. Vous pouvez appliquer plusieurs pragmas à une boucle, dans n'importe quel ordre, mais chacun doit être indiqué dans une instruction pragma distincte.

## <a name="see-also"></a>Voir aussi

[Parallélisation automatique et vectorisation automatique](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
