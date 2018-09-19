---
title: Évaluateur d’expression, erreur CXX0021 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0021
dev_langs:
- C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef765286d022b26aeed0ca98c9f43f94f5d17f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025774"
---
# <a name="expression-evaluator-error-cxx0021"></a>Évaluateur d'expression, erreur CXX0021

struct ou union utilisé comme scalaire

Une structure ou une union a été utilisée dans une expression, mais aucun élément n’a été spécifié.

Lors de la manipulation d’une structure ou une variable d’union, le nom de la variable peut apparaître seul, sans qualificateur de champ. Si une structure ou une union est utilisée dans une expression, il doit être qualifié avec l’élément spécifique que vous le souhaitez.

Spécifiez l’élément dont la valeur doit être utilisé dans l’expression.

Cette erreur est identique à CAN0021.