---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1223'
title: Erreur des outils Éditeur de liens LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: eb1937f253d324781834d0b6f465c79f7009787f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194057"
---
# <a name="linker-tools-error-lnk1223"></a>Erreur des outils Éditeur de liens LNK1223

fichier non valide ou endommagé : le fichier contient des contributions .pdata non valides

Pour les plateformes RISC qui utilisent des pdata, cette erreur survient si le compilateur a émis une section .pdata avec des entrées non triées.

Pour résoudre ce problème, essayez de compiler sans l’option [/GL (optimisation de l’ensemble du programme)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) activée. Les corps de fonction vides peuvent aussi provoquer cette erreur dans certains cas.
