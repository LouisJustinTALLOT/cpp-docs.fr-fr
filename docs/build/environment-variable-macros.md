---
title: Macros de variables d'environnement
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: 4691f89f1886b40637a0800ee8a6a94e4b4e06c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594296"
---
# <a name="environment-variable-macros"></a>Macros de variables d'environnement

NMAKE hérite des définitions de macros pour les variables d’environnement qui existent avant le début de la session. Si une variable a été définie dans l’environnement de système d’exploitation, il est disponible en tant qu’une macro NMAKE. Les noms hérités sont convertis en majuscules. L’héritage se produit avant le prétraitement. Utilisez l’option /E pour que les macros héritées de variables d’environnement pour remplacer toutes les macros portant le même nom dans le makefile.

Macros de variables d’environnement peuvent être redéfinis dans la session, et cela modifie la variable d’environnement correspondante. Vous pouvez également modifier les variables d’environnement avec la commande SET. Pour modifier une variable d’environnement dans une session à l’aide de la commande SET ne modifie pas la macro correspondante, toutefois.

Exemple :

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

Dans cet exemple, la modification `PATH` modifie la variable d’environnement correspondante `PATH`; il ajoute `\nonesuch` à votre chemin d’accès.

Si une variable d’environnement est définie en tant que chaîne qui serait syntaxiquement incorrecte dans un makefile, aucune macro n’est créée et aucun avertissement n’est généré. Si la valeur d’une variable contient un signe dollar ($), NMAKE l’interprète comme le début d’un appel de macro. À l’aide de la macro peut provoquer un comportement inattendu.

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](../build/special-nmake-macros.md)