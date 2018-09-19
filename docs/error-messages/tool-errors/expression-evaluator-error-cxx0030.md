---
title: Évaluateur d’expression, erreur CXX0030 | Microsoft Docs
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
ms.openlocfilehash: cb2921013d116b7d8f02e1e29380ca3cd14086b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102808"
---
# <a name="expression-evaluator-error-cxx0030"></a>Évaluateur d'expression, erreur CXX0030

expression non évaluée

Évaluateur d’expression du débogueur n’a pas pu obtenir une valeur pour l’expression comme écrite. Une cause probable est que l’expression fait référence à la mémoire qui est en dehors de l’espace d’adressage du programme (déréférencement d’un pointeur null n’est un exemple). Windows n’autorise pas l’accès à la mémoire qui est en dehors de l’espace d’adressage du programme.

Vous pouvez, si vous le souhaitez, réécrivez votre expression à l’aide de parenthèses pour contrôler l’ordre d’évaluation.

Cette erreur est identique à CAN0030.