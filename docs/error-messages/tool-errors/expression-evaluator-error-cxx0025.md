---
title: Évaluateur d’expression, erreur CXX0025 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0025
dev_langs:
- C++
helpviewer_keywords:
- CAN0025
- CXX0025
ms.assetid: 3e2fb541-63b3-46ac-9f93-3dadb253bcf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd89faa4de7b296d6a6771f857f3d16dbe2f94f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043701"
---
# <a name="expression-evaluator-error-cxx0025"></a>Évaluateur d'expression, erreur CXX0025

opérateur requiert struct/union

Un opérateur qui prend une expression de `struct` ou **union** type a été appliqué à une expression qui n’est pas un `struct` ou **union**.

Composants de classe, structure ou unions variables doivent avoir un nom qualifié complet. Composants ne peuvent pas être entrés sans spécification complète.

Cette erreur est identique à CAN0025.