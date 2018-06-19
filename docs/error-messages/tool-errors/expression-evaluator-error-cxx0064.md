---
title: Évaluateur d’expression, erreur CXX0064 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7964eac628fa89695d1757cff8b7b329fd7fe713
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302134"
---
# <a name="expression-evaluator-error-cxx0064"></a>Évaluateur d'expression, erreur CXX0064
ne peut pas définir le point d’arrêt sur fonction membre virtuelle liée  
  
 Un point d’arrêt a été définie sur une fonction membre virtuelle via un pointeur vers un objet, telle que :  
  
```  
pClass->vfunc( int );  
```  
  
 Un point d’arrêt peut être définie sur une fonction virtuelle en entrant la classe, par exemple :  
  
```  
Class::vfunc( int );  
```  
  
 Cette erreur est identique à CAN0064.