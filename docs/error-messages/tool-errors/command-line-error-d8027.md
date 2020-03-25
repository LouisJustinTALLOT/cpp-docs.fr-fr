---
title: Erreur de ligne de commande D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196883"
---
# <a name="command-line-error-d8027"></a>Erreur de ligne de commande D8027

Impossible d’exécuter’composant'

Le compilateur n’a pas pu exécuter le composant de compilateur ou l’éditeur de liens donné.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Mémoire insuffisante pour charger le composant. Si NMAKE a appelé le compilateur, exécutez le compilateur en dehors du Makefile.

1. Le système d’exploitation actuel n’a pas pu exécuter le composant. Assurez-vous que le chemin d’accès pointe vers les fichiers exécutables appropriés à votre système d’exploitation.

1. Le composant a été endommagé. Recopiez le composant à partir des disques de distribution, à l’aide du programme d’installation.

1. Une option a été spécifiée de manière incorrecte. Par exemple :

    ```
    cl /B1 file1.c
    ```
