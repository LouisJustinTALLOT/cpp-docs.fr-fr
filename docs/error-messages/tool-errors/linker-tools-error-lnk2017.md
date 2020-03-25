---
title: Erreur des outils Éditeur de liens LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194731"
---
# <a name="linker-tools-error-lnk2017"></a>Erreur des outils Éditeur de liens LNK2017

réadressage « Symbol » vers « segment » non valide sans/LARGEADDRESSAWARE : NO

Vous essayez de générer une image 64 bits avec des adresses 32 bits. Pour ce faire, vous devez effectuer les opérations suivantes :

- Utilisez une adresse de chargement fixe.

- Limitez l’image à 3 Go.

- Spécifiez [/LARGEADDRESSAWARE : no](../../build/reference/largeaddressaware-handle-large-addresses.md).
