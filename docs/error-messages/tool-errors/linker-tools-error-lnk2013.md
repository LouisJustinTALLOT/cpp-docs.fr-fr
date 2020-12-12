---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2013'
title: Erreur des outils Éditeur de liens LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 51b754e19656ad8ec7ef1686605086b6e4a41853
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338463"
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013

dépassement de la correction du type de correction. La cible’Symbol Name’est hors limites

L’éditeur de liens ne peut pas contenir l’adresse ou le décalage nécessaire dans l’instruction donnée, car le symbole cible est trop éloigné de l’emplacement de l’instruction.

Vous pouvez résoudre ce problème en créant plusieurs images ou à l’aide de l’option [/Order](../../build/reference/order-put-functions-in-order.md) afin que l’instruction et la cible soient plus proches.

Lorsque le nom du symbole est un symbole défini par l’utilisateur (et non un symbole généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :

- Modifiez la fonction statique pour qu’elle soit non statique.

- Renommez la section de code contenant la fonction statique pour qu’elle soit identique à celle de l’appelant.

Utilisez `DUMPBIN /SYMBOLS` pour voir si une fonction est statique.
