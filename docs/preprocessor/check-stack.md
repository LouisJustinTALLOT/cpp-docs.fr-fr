---
title: check_stack
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 49477a3b39db17047f349e341bd05c04954c964c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023371"
---
# <a name="checkstack"></a>check_stack
Indique au compilateur de désactiver les tests de pile si `off` (ou `-`) est spécifié, ou pour activer les tests de pile si `on` (ou `+`) est spécifié.

## <a name="syntax"></a>Syntaxe

```
#pragma check_stack([ {on | off}] )
#pragma check_stack{+ | -}
```

## <a name="remarks"></a>Notes

Si aucun argument n’est fourni, les tests de pile sont traités en fonction de la valeur par défaut. Ce pragma est appliqué à la première fonction définie après détection du pragma. Les tests de pile ne font partie ni des macros, ni des fonctions générées inline.

Si vous ne fournissez pas d’argument pour le **check_stack** pragma, contrôle de pile rétablit le comportement spécifié sur la ligne de commande. Pour plus d’informations, consultez [référence du compilateur](../build/reference/compiler-options.md). L’interaction entre le `#pragma check_stack` et [/GS](../build/reference/gs-control-stack-checking-calls.md) option est résumée dans le tableau suivant.

### <a name="using-the-checkstack-pragma"></a>Utilisation du pragma check_stack

|Syntaxe|Compilé avec<br /><br /> Option /Gs ?|Action|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` ou<br /><br /> `#pragma check_stack`|Oui|Désactive la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack( )` ou<br /><br /> `#pragma check_stack`|Non|Active la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack(on)`<br /><br /> Ou `#pragma check_stack +`|Oui ou non|Active la vérification de la pile pour les fonctions qui suivent|
|`#pragma check_stack(off)`<br /><br /> Ou `#pragma check_stack -`|Oui ou non|Désactive la vérification de la pile pour les fonctions qui suivent|

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)