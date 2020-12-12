---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0021'
title: Évaluateur d'expression, erreur CXX0021
ms.date: 11/04/2016
f1_keywords:
- CXX0021
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
ms.openlocfilehash: 0ff42ec52ab19c726b0e1752fbb47f81da588533
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228133"
---
# <a name="expression-evaluator-error-cxx0021"></a>Évaluateur d'expression, erreur CXX0021

struct ou Union utilisé comme scalaire

Une structure ou une Union a été utilisée dans une expression, mais aucun élément n’a été spécifié.

Lors de la manipulation d’une variable de structure ou d’Union, le nom de la variable peut s’afficher seul, sans qualificateur de champ. Si une structure ou une Union est utilisée dans une expression, elle doit être qualifiée avec l’élément spécifique souhaité.

Spécifiez l’élément dont la valeur doit être utilisée dans l’expression.

Cette erreur est identique à CAN0021.
