---
title: Erreur BSCMAKE BK1509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 091fab63737c7ee1b3b85753a354bb7214cfa411
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025241"
---
# <a name="bscmake-error-bk1509"></a>Erreur BSCMAKE BK1509

espace du tas insuffisant

BSCMAKE a manqué de mémoire, y compris la mémoire virtuelle.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Libérez de l’espace disque.

1. Augmenter la taille du fichier d’échange.

1. Augmenter la taille du fichier d’échange de Windows.

1. Réduire la mémoire avec BSCMAKE, à l’aide de /Ei ou/es à éviter certains fichiers d’entrée ou /Em pour éliminer les corps de la macro.