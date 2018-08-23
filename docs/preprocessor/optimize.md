---
title: optimiser | Microsoft Docs
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
ms.openlocfilehash: 8222d909ad23157b4e3ed32a6920abadd77709b6
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539417"
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
|*y*|Génère des pointeurs de frame sur la pile du programme.|  
  
Ce sont les mêmes lettres que celui utilisés avec le [/O](../build/reference/o-options-optimize-code.md) options du compilateur. Par exemple, le pragma suivant équivaut à l'option du compilateur `/Os` :  
  
```  
#pragma optimize( "ts", on )  
```  
  
À l’aide de la **optimiser** pragma avec la chaîne vide (**» «**) est une forme spéciale de la directive :  
  
Lorsque vous utilisez le *hors* paramètre, il active les optimisations, répertoriées dans le tableau précédemment dans cette rubrique, hors tension.  
  
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