---
title: Optimisation de l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49660bdc6d2eb84e6e1bbaeb5ebf0d57e484e9e1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687874"
---
# <a name="optimizing-inline-assembly"></a>Optimisation de l'assembly inline

**Section spécifique à Microsoft**

La présence d'un bloc `__asm` dans une fonction affecte l'optimisation de plusieurs façons. D'abord, le compilateur ne tente pas d'optimiser le bloc `__asm` lui-même. Ce que vous écrivez dans le langage assembleur est exactement ce que vous obtenez. Ensuite, la présence d'un bloc `__asm` affecte le stockage des variables du registre. Le compilateur évite d'enregistrer les variables dans un bloc `__asm` si le contenu du registre est modifié par le bloc `__asm`. Enfin, certaines optimisations au niveau de la fonction seront affectées par l'inclusion du langage assembleur dans une fonction.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>