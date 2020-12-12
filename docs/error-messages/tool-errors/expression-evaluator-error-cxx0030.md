---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0030'
title: Évaluateur d'expression, erreur CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: d9679d260ce81c2cb9bb8be4c082ffe8c1cfc6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237425"
---
# <a name="expression-evaluator-error-cxx0030"></a>Évaluateur d'expression, erreur CXX0030

expression non evaluatable

L’évaluateur d’expression du débogueur n’a pas pu obtenir une valeur pour l’expression telle qu’elle a été écrite. La cause la plus probable est que l’expression fait référence à la mémoire qui se trouve en dehors de l’espace d’adressage du programme (le déréférencement d’un pointeur null est un exemple). Windows n’autorise pas l’accès à la mémoire qui se trouve en dehors de l’espace d’adressage du programme.

Vous souhaiterez peut-être réécrire votre expression en utilisant des parenthèses pour contrôler l’ordre d’évaluation.

Cette erreur est identique à CAN0030.
