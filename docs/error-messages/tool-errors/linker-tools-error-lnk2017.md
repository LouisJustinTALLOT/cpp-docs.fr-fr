---
title: Erreur des LNK2017 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022448"
---
# <a name="linker-tools-error-lnk2017"></a>Erreur des outils Éditeur de liens LNK2017

réadressage 'symbole' vers 'segment' non valide sans/LARGEADDRESSAWARE : no

Vous tentez de créer une image 64 bits avec des adresses 32 bits. Pour ce faire, vous devez :

- Utiliser une adresse de chargement fixe.

- Restreindre l’image à 3 Go.

- Spécifiez [/LARGEADDRESSAWARE : no](../../build/reference/largeaddressaware-handle-large-addresses.md).