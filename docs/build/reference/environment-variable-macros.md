---
description: En savoir plus sur les macros de Environment-Variable
title: Macros de variables d'environnement
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: b7beaf8f3e98ea7447d798041f7531ed5da671ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192588"
---
# <a name="environment-variable-macros"></a>Macros de variables d'environnement

NMAKE hérite des définitions de macro pour les variables d’environnement qui existent avant le début de la session. Si une variable a été définie dans l’environnement du système d’exploitation, elle est disponible sous la forme d’une macro NMAKE. Les noms hérités sont convertis en majuscules. L’héritage se produit avant le prétraitement. Utilisez l’option/E pour faire en sorte que les macros héritées des variables d’environnement remplacent toutes les macros portant le même nom dans le Makefile.

Les macros de variables d’environnement peuvent être redéfinies dans la session, ce qui modifie la variable d’environnement correspondante. Vous pouvez également modifier les variables d’environnement à l’aide de la commande SET. Toutefois, l’utilisation de la commande SET pour modifier une variable d’environnement dans une session ne modifie pas la macro correspondante.

Par exemple :

```
PATH=$(PATH);\nonesuch

all:
    echo %%PATH%%
```

Dans cet exemple, la modification de `PATH` change la variable d’environnement correspondante `PATH` . elle est ajoutée `\nonesuch` à votre chemin d’accès.

Si une variable d’environnement est définie comme une chaîne qui serait syntaxiquement incorrecte dans un Makefile, aucune macro n’est créée et aucun avertissement n’est généré. Si la valeur d’une variable contient un signe dollar ($), NMAKE l’interprète comme le début d’un appel de macro. L’utilisation de la macro peut entraîner un comportement inattendu.

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
