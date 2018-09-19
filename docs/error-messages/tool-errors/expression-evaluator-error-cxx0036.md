---
title: Évaluateur d’expression, erreur CXX0036 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2d82a1254a11dbda3164ea1c350dc14e2b1a122
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050110"
---
# <a name="expression-evaluator-error-cxx0036"></a>Évaluateur d'expression, erreur CXX0036

contexte incorrect {...} spécification

Ce message peut être généré par plusieurs erreurs dans l’utilisation de l’opérateur de contexte (**{}**).

- La syntaxe de l’opérateur de contexte (**{}**) a été donné de façon incorrecte.

     La syntaxe de l’opérateur de contexte est :

     {*fonction*,*module*,*dll*}*expression*

     Spécifie le contexte de *expression*. L’opérateur de contexte a la même priorité et l’utilisation en tant qu’un cast de type.

     Virgules de fin peuvent être omis. Si un des *fonction*, *module*, ou *dll* contient une virgule littérale, vous devez placer l’intégralité du nom entre parenthèses.

- Le nom de fonction a été mal orthographié ou n’existe pas dans la bibliothèque de liens dynamiques ou le module spécifié.

     Étant donné que C est un langage qui respecte la casse, *fonction* doivent figurer dans la casse car il est défini dans la source.

- Le module ou la DLL est introuvable.

     Vérifiez le nom de chemin d’accès complet du module spécifié ou de la DLL.

Cette erreur est identique à CAN0036.