---
title: Évaluateur d’expression, erreur CXX0030 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669c585c637129c1fb6a480d91b31e5a1264fd22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298114"
---
# <a name="expression-evaluator-error-cxx0030"></a>Évaluateur d'expression, erreur CXX0030
expression non évaluée  
  
 Évaluateur d’expression du débogueur n’a pas pu obtenir une valeur pour l’expression lors de l’écriture. Une des causes possibles sont que l’expression fait référence à la mémoire qui est en dehors de l’espace d’adressage du programme (déréférencement d’un pointeur null est d’un exemple). Windows n’autorise pas l’accès à la mémoire qui est en dehors de l’espace d’adressage du programme.  
  
 Vous souhaiterez Réécrivez votre expression utilisant des parenthèses pour contrôler l’ordre d’évaluation.  
  
 Cette erreur est identique à CAN0030.