---
title: Évaluateur d’expression, erreur CXX0029 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0029
dev_langs:
- C++
helpviewer_keywords:
- CXX0029
- CAN0029
ms.assetid: 562b2132-e9cb-4591-a5bf-bc7179a7f40e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 687708db71eedf9b8f62dc88efc1bfe473cde1d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017012"
---
# <a name="expression-evaluator-error-cxx0029"></a>Évaluateur d'expression, erreur CXX0029

pointeur non struct

L’opérateur de sélection de membre (**->**) a été appliqué à une expression qui n’est pas un pointeur vers une structure.

Vérifiez que l’expression entière est entre parenthèses correctement, ou effectuer un cast de type de l’expression d’adresse pour le type de pointeur de structure approprié.

Cette erreur est identique à CAN0029.