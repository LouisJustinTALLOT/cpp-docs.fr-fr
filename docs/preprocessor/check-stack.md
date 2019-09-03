---
title: check_stack, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 4c976692ec36cedcb73825ee0cc7093736a3a3dc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216126"
---
# <a name="check_stack-pragma"></a>check_stack, pragma

Indique au compilateur de désactiver les sondes de pile si la valeur OFF **-** (ou) est spécifiée, ou d’activer les sondes de pile si **+** **on** (ou) est spécifié.

## <a name="syntax"></a>Syntaxe

> **#pragma check_stack (** [{ **on** | **off** }] **)** \
> **#pragma check_stack** { **+**  |  **-** }

## <a name="remarks"></a>Notes

Ce pragma est appliqué à la première fonction définie après détection du pragma. Les tests de pile ne font partie ni des macros, ni des fonctions générées inline.

Si vous ne fournissez pas d’argument pour le pragma **check_stack** , la vérification de pile revient au comportement spécifié sur la ligne de commande. Pour plus d’informations, consultez [Options du compilateur](../build/reference/compiler-options.md). L’interaction des `#pragma check_stack` et de l’option [/GS](../build/reference/gs-control-stack-checking-calls.md) est résumée dans le tableau suivant.

### <a name="using-the-check_stack-pragma"></a>Utilisation du pragma check_stack

|Syntaxe|Compilé avec<br /><br /> Option /Gs ?|Action|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` ou<br /><br /> `#pragma check_stack`|Oui|Désactive la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack( )` ou<br /><br /> `#pragma check_stack`|Non|Active la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack(on)`<br /><br /> ni`#pragma check_stack +`|Oui ou non|Active la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack(off)`<br /><br /> ni`#pragma check_stack -`|Oui ou non|Désactive la vérification de la pile pour les fonctions qui suivent|

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
