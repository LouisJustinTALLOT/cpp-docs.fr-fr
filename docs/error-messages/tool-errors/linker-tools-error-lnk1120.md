---
title: Erreur des outils Éditeur de liens LNK1120
description: Décrit l’erreur de l’éditeur de liens LNK1120, qui indique le nombre d’erreurs de symbole externe non résolues dans le lien.
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626580"
---
# <a name="linker-tools-error-lnk1120"></a>Erreur des outils Éditeur de liens LNK1120

> *nombre* de externes non résolus

Erreur LNK1120 indique le nombre d’erreurs de [symbole externe non résolues](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol) dans le lien actuel.

Chaque symbole externe non résolu est d’abord signalé par une erreur [LNK2001](linker-tools-error-lnk2001.md) ou [LNK2019](linker-tools-error-lnk2019.md) . Le message LNK1120 est le dernier et affiche le nombre d’erreurs de symbole non résolu.

> [!IMPORTANT]
> **Vous n’avez pas besoin de corriger cette erreur.** Cette erreur disparaît lorsque vous corrigez toutes les erreurs LNK2001 et LNK2019 de l’éditeur de liens avant celles-ci dans la sortie de génération. Résolvez toujours les problèmes à partir de la première erreur signalée. Les erreurs ultérieures peuvent être dues à des versions antérieures et disparaître lorsque les erreurs précédentes sont corrigées.
