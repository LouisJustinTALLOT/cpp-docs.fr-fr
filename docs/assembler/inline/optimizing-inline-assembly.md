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
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169264"
---
# <a name="optimizing-inline-assembly"></a>Optimisation de l'assembly inline

**Section spécifique de Microsoft**

La présence d'un bloc `__asm` dans une fonction affecte l'optimisation de plusieurs façons. D'abord, le compilateur ne tente pas d'optimiser le bloc `__asm` lui-même. Ce que vous écrivez dans le langage assembleur est exactement ce que vous obtenez. Ensuite, la présence d'un bloc `__asm` affecte le stockage des variables du registre. Le compilateur évite d'enregistrer les variables dans un bloc `__asm` si le contenu du registre est modifié par le bloc `__asm`. Enfin, certaines optimisations au niveau de la fonction seront affectées par l'inclusion du langage assembleur dans une fonction.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
