---
title: Erreur des outils Éditeur de liens LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299066"
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013

type correction débordement. Cible 'symbol name' est hors limites

L’éditeur de liens ne rentrent pas l’offset ou une adresse nécessaire sur l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.

Vous pouvez résoudre ce problème en créant plusieurs images ou en utilisant le [/Order](../../build/reference/order-put-functions-in-order.md) option pour l’instruction et la cible rapprocher.

Lorsque le nom du symbole est un symbole défini par l’utilisateur (et non généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :

- Modifier la fonction statique pour être non statique.

- Renommer la section de code contenant la fonction statique pour être le même que l’appelant.

Utilisez `DUMPBIN /SYMBOLS`, pour voir si une fonction est statique.