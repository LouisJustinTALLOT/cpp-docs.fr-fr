---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1033'
title: Erreur irrécupérable NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: e616e98a21c92137fab4b167318a9305a2175bb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272134"
---
# <a name="nmake-fatal-error-u1033"></a>Erreur irrécupérable NMAKE U1033

erreur de syntaxe : 'String’inattendu

La chaîne ne fait pas partie de la syntaxe valide pour un Makefile.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Si le jeu de parenthèses angulaires () de fermeture d' **<<** un fichier Inline ne se trouve pas au début d’une ligne, l’erreur suivante se produit :

    ```
    syntax error : 'EOF' unexpected
    ```

1. Si une définition de macro dans le makefile contient un signe égal ( **=** ) sans nom précédent ou si le nom défini est une macro qui se développe en rien, l’erreur suivante se produit :

    ```
    syntax error : '=' unexpected
    ```

1. Si le point-virgule (**;**) d’une ligne de commentaire dans TOOLS.INI ne se trouve pas au début de la ligne, l’erreur suivante se produit :

    ```
    syntax error : ';' unexpected
    ```

1. Si le Makefile a été mis en forme par un traitement de texte, l’erreur suivante peut se produire :

    ```
    syntax error : ':' unexpected
    ```
