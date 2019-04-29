---
title: Erreur BSCMAKE BK1509
ms.date: 11/04/2016
f1_keywords:
- BK1509
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
ms.openlocfilehash: 384f202ea3eb969da2ce3a3b82209c383009c62e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279526"
---
# <a name="bscmake-error-bk1509"></a>Erreur BSCMAKE BK1509

espace du tas insuffisant

BSCMAKE a manqué de mémoire, y compris la mémoire virtuelle.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace disque.

1. Augmenter la taille du fichier d’échange.

1. Augmenter la taille du fichier d’échange de Windows.

1. Réduire la mémoire avec BSCMAKE, à l’aide de /Ei ou/es à éviter certains fichiers d’entrée ou /Em pour éliminer les corps de la macro.