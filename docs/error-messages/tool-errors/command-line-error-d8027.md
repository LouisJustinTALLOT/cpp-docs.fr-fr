---
title: Erreur de ligne de commande D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526798"
---
# <a name="command-line-error-d8027"></a>Erreur de ligne de commande D8027

Impossible d’exécuter 'composant'

Le compilateur n’a pas pu exécuter le composant de compilateur donné ou d’un éditeur de liens.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Mémoire insuffisante pour charger le composant. Si NMAKE a appelé le compilateur, exécutez le compilateur en dehors du makefile.

1. Le système d’exploitation actuel n’a pas pu exécuter le composant. Assurez-vous que les points de chemin d’accès aux fichiers exécutables approprié à votre système d’exploitation.

1. Le composant a été endommagé. Recopiez le composant à partir de disques de distribution, à l’aide du programme d’installation.

1. Une option a été spécifiée correctement. Exemple :

    ```
    cl /B1 file1.c
    ```