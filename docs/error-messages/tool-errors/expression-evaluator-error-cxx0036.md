---
title: Évaluateur d'expression, erreur CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: d7961d92760cc5ac325b4bc9f187d4ee2298479a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397027"
---
# <a name="expression-evaluator-error-cxx0036"></a>Évaluateur d'expression, erreur CXX0036

contexte incorrect {...} spécification

Ce message peut être généré par plusieurs erreurs dans l’utilisation de l’opérateur de contexte (**{}**).

- La syntaxe de l’opérateur de contexte (**{}**) a été donné de façon incorrecte.

   La syntaxe de l’opérateur de contexte est :

     {*function*,*module*,*dll*}*expression*

   Spécifie le contexte de *expression*. L’opérateur de contexte a la même priorité et l’utilisation en tant qu’un cast de type.

   Virgules de fin peuvent être omis. Si un des *fonction*, *module*, ou *dll* contient une virgule littérale, vous devez placer l’intégralité du nom entre parenthèses.

- Le nom de fonction a été mal orthographié ou n’existe pas dans la bibliothèque de liens dynamiques ou le module spécifié.

   Étant donné que C est un langage qui respecte la casse, *fonction* doivent figurer dans la casse car il est défini dans la source.

- Le module ou la DLL est introuvable.

   Vérifiez le nom de chemin d’accès complet du module spécifié ou de la DLL.

Cette erreur est identique à CAN0036.