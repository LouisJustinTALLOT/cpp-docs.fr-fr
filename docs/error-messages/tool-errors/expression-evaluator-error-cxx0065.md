---
title: Évaluateur d’expression, erreur CXX0065 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297535"
---
# <a name="expression-evaluator-error-cxx0065"></a>Évaluateur d'expression, erreur CXX0065
variable a besoin du frame de pile  
  
 Une expression contient une variable qui existe dans la portée actuelle, mais n’a pas encore été créée.  
  
 Cette erreur peut se produire lorsque vous avez exécuté le code dans le prologue d’une fonction, mais pas encore configurer le frame de pile pour la fonction, ou si vous avez exécuté le code dans le code de sortie pour la fonction.  
  
 Parcourez le code de prologue jusqu'à ce que le frame de pile a été configuré avant d’évaluer l’expression.  
  
 Cette erreur est identique à CAN0065.