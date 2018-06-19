---
title: check_stack | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
dev_langs:
- C++
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b393030961aa4695a16a9b50d49d0cae64cc4e0c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849767"
---
# <a name="checkstack"></a>check_stack
Indique au compilateur pour désactiver les tests de pile si **hors** (ou **-**) est spécifié, ou pour activer les tests de pile si **sur** (ou **+**) est spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | -}  
```  
  
## <a name="remarks"></a>Notes  
 Si aucun argument n’est fourni, les tests de pile sont traités en fonction de la valeur par défaut. Ce pragma est appliqué à la première fonction définie après détection du pragma. Les tests de pile ne font partie ni des macros, ni des fonctions générées inline.  
  
 Si vous ne fournissez pas d’argument pour le **check_stack** pragma, la vérification de la pile rétablit le comportement spécifié sur la ligne de commande. Pour plus d’informations, consultez [référence du compilateur](../build/reference/compiler-options.md). L’interaction entre le **#pragma check_stack** et [/Gs](../build/reference/gs-control-stack-checking-calls.md) option est résumée dans le tableau suivant.  
  
### <a name="using-the-checkstack-pragma"></a>Utilisation du pragma check_stack  
  
|Syntaxe|Compilé avec<br /><br /> Option /Gs ?|Action|  
|------------|------------------------------------|------------|  
|**#pragma check_stack ()** ou<br /><br /> **#pragma check_stack**|Oui|Désactive la vérification de la pile pour les fonctions qui suivent|  
|**#pragma check_stack ()** ou<br /><br /> **#pragma check_stack**|Non|Active la vérification de la pile pour les fonctions qui suivent|  
|**#pragma check_stack(on)**<br /><br /> ou **#pragma check_stack +**|Oui ou non|Active la vérification de la pile pour les fonctions qui suivent|  
|**#pragma check_stack(off)**<br /><br /> ou **#pragma check_stack -**|Oui ou non|Désactive la vérification de la pile pour les fonctions qui suivent|  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)