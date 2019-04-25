---
title: Optimisation de l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166878"
---
# <a name="optimizing-inline-assembly"></a>Optimisation de l'assembly inline

**Section spécifique à Microsoft**

La présence d'un bloc `__asm` dans une fonction affecte l'optimisation de plusieurs façons. D'abord, le compilateur ne tente pas d'optimiser le bloc `__asm` lui-même. Ce que vous écrivez dans le langage assembleur est exactement ce que vous obtenez. Ensuite, la présence d'un bloc `__asm` affecte le stockage des variables du registre. Le compilateur évite d'enregistrer les variables dans un bloc `__asm` si le contenu du registre est modifié par le bloc `__asm`. Enfin, certaines optimisations au niveau de la fonction seront affectées par l'inclusion du langage assembleur dans une fonction.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>