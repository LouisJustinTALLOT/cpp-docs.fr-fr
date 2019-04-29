---
title: Évaluateur d'expression, erreur CXX0021
ms.date: 11/04/2016
f1_keywords:
- CXX0021
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
ms.openlocfilehash: 373829e7200a556b3f832b1da127b4e33aa75749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359876"
---
# <a name="expression-evaluator-error-cxx0021"></a>Évaluateur d'expression, erreur CXX0021

struct ou union utilisé comme scalaire

Une structure ou une union a été utilisée dans une expression, mais aucun élément n’a été spécifié.

Lors de la manipulation d’une structure ou une variable d’union, le nom de la variable peut apparaître seul, sans qualificateur de champ. Si une structure ou une union est utilisée dans une expression, il doit être qualifié avec l’élément spécifique que vous le souhaitez.

Spécifiez l’élément dont la valeur doit être utilisé dans l’expression.

Cette erreur est identique à CAN0021.