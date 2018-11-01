---
title: Erreur des outils Éditeur de liens LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641456"
---
# <a name="linker-tools-error-lnk2017"></a>Erreur des outils Éditeur de liens LNK2017

réadressage 'symbole' vers 'segment' non valide sans/LARGEADDRESSAWARE : no

Vous tentez de créer une image 64 bits avec des adresses 32 bits. Pour ce faire, vous devez :

- Utiliser une adresse de chargement fixe.

- Restreindre l’image à 3 Go.

- Spécifiez [/LARGEADDRESSAWARE : no](../../build/reference/largeaddressaware-handle-large-addresses.md).