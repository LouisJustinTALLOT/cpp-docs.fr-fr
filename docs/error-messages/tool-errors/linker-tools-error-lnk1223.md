---
title: Erreur des outils Éditeur de liens LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195030"
---
# <a name="linker-tools-error-lnk1223"></a>Erreur des outils Éditeur de liens LNK1223

fichier non valide ou endommagé : le fichier contient des contributions .pdata non valides

Pour les plateformes RISC qui utilisent des pdata, cette erreur survient si le compilateur a émis une section .pdata avec des entrées non triées.

Pour résoudre ce problème, essayez de compiler sans l’option [/GL (optimisation de l’ensemble du programme)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) activée. Les corps de fonction vides peuvent aussi provoquer cette erreur dans certains cas.
