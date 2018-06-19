---
title: optimiser | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bff0e4cc40bfa0e355f348c02f01cb0c7445b596
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849247"
---
# <a name="optimize"></a>optimize
Spécifie les optimisations à effectuer sur une base fonction par fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Notes  
 Le **optimiser** pragma doit apparaître en dehors d’une fonction et prend effet à la première fonction définie après le pragma. Le **sur** et **hors** arguments activer des options spécifiées dans le *-liste d’optimisation* ou désactiver.  
  
 Le *-liste d’optimisation* peut être zéro ou plusieurs des paramètres indiqués dans le tableau suivant.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Paramètres du pragma optimize  
  
|Paramètre(s)|Type d'optimisation|  
|--------------------|--------------------------|  
|**g**|Active les optimisations globales.|  
|**s** ou **t**|Spécifie des séquences courtes ou rapides de code machine.|  
|**y**|Génère des pointeurs de frame sur la pile du programme.|  
  
 Ce sont les mêmes lettres que celui utilisés avec les [/O](../build/reference/o-options-optimize-code.md) options du compilateur. Par exemple, le pragma suivant équivaut à la **/Os** option du compilateur :  
  
```  
#pragma optimize( "ts", on )  
```  
  
 À l’aide de la **optimiser** pragma avec la chaîne vide (**» «**) est une forme particulière de la directive :  
  
 Lorsque vous utilisez la **hors** paramètre, il désactive les optimisations, répertoriées dans le tableau précédent de cette rubrique, hors tension.  
  
 Lorsque vous utilisez la **sur** paramètre, il réinitialise les optimisations à celles que vous avez spécifié avec la [/O](../build/reference/o-options-optimize-code.md) option du compilateur.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)