---
title: Évaluateur d'expression, erreur CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195498"
---
# <a name="expression-evaluator-error-cxx0036"></a>Évaluateur d'expression, erreur CXX0036

contexte incorrect {...} specification

Ce message peut être généré par l’une des erreurs suivantes dans l’utilisation de l’opérateur de contexte ( **{}** ).

- La syntaxe de l’opérateur de contexte ( **{}** ) a été incorrecte.

   La syntaxe de l’opérateur de contexte est la suivante :

     {*fonction*,*module*,*dll*} *expression*

   Spécifie le contexte de l' *expression*. L’opérateur de contexte a la même priorité et utilisation qu’un cast de type.

   Les virgules de fin peuvent être omises. Si l’une des *fonctions*, *modules*ou *dll* contient une virgule littérale, vous devez placer le nom entier entre parenthèses.

- Le nom de la fonction n’a pas été orthographié correctement ou n’existe pas dans le module ou la bibliothèque de liens dynamiques spécifiés.

   Étant donné que C est un langage qui respecte la casse, la *fonction* doit être fournie dans le cas exact, car elle est définie dans la source.

- Le module ou la DLL est introuvable.

   Vérifiez le nom du chemin d’accès complet du module ou de la DLL spécifiés.

Cette erreur est identique à CAN0036.
