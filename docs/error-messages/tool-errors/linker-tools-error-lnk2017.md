---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2017'
title: Erreur des outils Éditeur de liens LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: e4215d7c1730f85f43c2440163fa03ad97c741e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338453"
---
# <a name="linker-tools-error-lnk2017"></a>Erreur des outils Éditeur de liens LNK2017

réadressage « Symbol » vers « segment » non valide sans/LARGEADDRESSAWARE : NO

Vous essayez de générer une image 64 bits avec des adresses 32 bits. Pour ce faire, vous devez effectuer les opérations suivantes :

- Utilisez une adresse de chargement fixe.

- Limitez l’image à 3 Go.

- Spécifiez [/LARGEADDRESSAWARE : no](../../build/reference/largeaddressaware-handle-large-addresses.md).
