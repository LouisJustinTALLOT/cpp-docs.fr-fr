---
title: Erreur des LNK2013 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04ce4ca8079317da090cf05d43f41e4e40a6b19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041738"
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013

type correction débordement. Cible 'symbol name' est hors limites

L’éditeur de liens ne rentrent pas l’offset ou une adresse nécessaire sur l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.

Vous pouvez résoudre ce problème en créant plusieurs images ou en utilisant le [/Order](../../build/reference/order-put-functions-in-order.md) option pour l’instruction et la cible rapprocher.

Lorsque le nom du symbole est un symbole défini par l’utilisateur (et non généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :

- Modifier la fonction statique pour être non statique.

- Renommer la section de code contenant la fonction statique pour être le même que l’appelant.

Utilisez `DUMPBIN /SYMBOLS`, pour voir si une fonction est statique.