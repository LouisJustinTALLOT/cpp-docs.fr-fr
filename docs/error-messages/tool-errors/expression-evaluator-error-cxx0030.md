---
title: Évaluateur d'expression, erreur CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195615"
---
# <a name="expression-evaluator-error-cxx0030"></a>Évaluateur d'expression, erreur CXX0030

expression non evaluatable

L’évaluateur d’expression du débogueur n’a pas pu obtenir une valeur pour l’expression telle qu’elle a été écrite. La cause la plus probable est que l’expression fait référence à la mémoire qui se trouve en dehors de l’espace d’adressage du programme (le déréférencement d’un pointeur null est un exemple). Windows n’autorise pas l’accès à la mémoire qui se trouve en dehors de l’espace d’adressage du programme.

Vous souhaiterez peut-être réécrire votre expression en utilisant des parenthèses pour contrôler l’ordre d’évaluation.

Cette erreur est identique à CAN0030.
