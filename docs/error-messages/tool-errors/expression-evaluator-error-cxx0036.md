---
title: Évaluateur d’expression, erreur CXX0036 | Documents Microsoft
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
ms.openlocfilehash: 18e1bf3cda85d7b3d64d51279688a52cec5c0336
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301682"
---
# <a name="expression-evaluator-error-cxx0036"></a>Évaluateur d'expression, erreur CXX0036
contexte incorrect {...} spécification  
  
 Ce message peut être généré par plusieurs erreurs dans l’utilisation de l’opérateur de contexte (**{}**).  
  
-   La syntaxe de l’opérateur de contexte (**{}**) a été donné de façon incorrecte.  
  
     La syntaxe de l’opérateur de contexte est la suivante :  
  
     {*fonction*,*module*,*dll*}*expression*  
  
     Spécifie le contexte de *expression*. L’opérateur de contexte a la même priorité et l’utilisation en tant qu’un cast de type.  
  
     Virgules de fin peuvent être omis. Si une des *fonction*, *module*, ou *dll* contient une virgule littérale, vous devez placer le nom entier entre parenthèses.  
  
-   Le nom de la fonction a été mal orthographié ou n’existe pas dans le module spécifié ou de la bibliothèque de liens dynamiques.  
  
     Étant donné que C est un langage qui respecte la casse, *fonction* doivent figurer dans la casse exacte telle qu’elle est définie dans la source.  
  
-   Le module ou la DLL est introuvable.  
  
     Vérifiez le nom de chemin d’accès complet du module spécifié ou de la DLL.  
  
 Cette erreur est identique à CAN0036.