---
title: Erreur des outils Éditeur de liens LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242823"
---
# <a name="linker-tools-error-lnk1223"></a>Erreur des outils Éditeur de liens LNK1223

fichier non valide ou endommagé : le fichier contient des contributions .pdata non valides

Pour les plateformes RISC qui utilisent des pdata, cette erreur survient si le compilateur a émis une section .pdata avec des entrées non triées.

Pour résoudre ce problème, essayez de compiler sans [/GL (Whole Program Optimization)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) activé. Les corps de fonction vides peuvent aussi provoquer cette erreur dans certains cas.