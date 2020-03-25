---
title: Erreur des outils Éditeur de liens LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194744"
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013

dépassement de la correction du type de correction. La cible’Symbol Name’est hors limites

L’éditeur de liens ne peut pas contenir l’adresse ou le décalage nécessaire dans l’instruction donnée, car le symbole cible est trop éloigné de l’emplacement de l’instruction.

Vous pouvez résoudre ce problème en créant plusieurs images ou à l’aide de l’option [/Order](../../build/reference/order-put-functions-in-order.md) afin que l’instruction et la cible soient plus proches.

Lorsque le nom du symbole est un symbole défini par l’utilisateur (et non un symbole généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :

- Modifiez la fonction statique pour qu’elle soit non statique.

- Renommez la section de code contenant la fonction statique pour qu’elle soit identique à celle de l’appelant.

Utilisez `DUMPBIN /SYMBOLS`pour voir si une fonction est statique.
