---
title: Évaluateur d’expression, erreur CXX0039 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297766"
---
# <a name="expression-evaluator-error-cxx0039"></a>Évaluateur d'expression, erreur CXX0039
symbole est ambigu  
  
 L’évaluateur d’expression C ne peut pas déterminer quelle instance d’un symbole à utiliser dans une expression. Le symbole apparaît plusieurs fois dans l’arborescence d’héritage.  
  
 Vous devez utiliser l’opérateur de résolution de portée (`::`) pour spécifier explicitement l’instance à utiliser dans l’expression.  
  
 Cette erreur est identique à CAN0039.