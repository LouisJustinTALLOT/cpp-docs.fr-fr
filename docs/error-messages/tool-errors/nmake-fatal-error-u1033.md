---
title: Erreur irrécupérable NMAKE U1033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066376"
---
# <a name="nmake-fatal-error-u1033"></a>Erreur irrécupérable NMAKE U1033

Erreur de syntaxe : 'string' inattendu

La chaîne ne fait pas partie de la syntaxe valide d’un makefile.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Si la valeur de la fermeture des crochets pointus (**<<**) pour un fichier inline ne sont pas au début d’une ligne, l’erreur suivante se produit :

    ```
    syntax error : 'EOF' unexpected
    ```

1. Si une définition de macro dans le makefile contenue un signe égal (**=**) sans précédente nom ou si le nom en cours est une macro se développe vers rien, l’erreur suivante se produit :

    ```
    syntax error : '=' unexpected
    ```

1. Si le point-virgule (**;**) dans une ligne de commentaire dans les outils. INI n’est pas au début de la ligne, l’erreur suivante se produit :

    ```
    syntax error : ';' unexpected
    ```

1. Si le makefile a été mis en forme par un traitement de texte, l’erreur suivante peut se produire :

    ```
    syntax error : ':' unexpected
    ```