---
description: 'En savoir plus sur : optimisation de l’assembly inline'
title: Optimisation de l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: 62c4dad85128089cdcf85f4156884747f928338f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122094"
---
# <a name="optimizing-inline-assembly"></a>Optimisation de l'assembly inline

**Spécifique à Microsoft**

La présence d’un **`__asm`** bloc dans une fonction affecte l’optimisation de plusieurs façons. Tout d’abord, le compilateur n’essaie pas d’optimiser le **`__asm`** bloc lui-même. Ce que vous écrivez dans le langage assembleur est exactement ce que vous obtenez. Deuxièmement, la présence d’un **`__asm`** bloc affecte le stockage des variables de registre. Le compilateur évite d’inscrire des variables dans un **`__asm`** bloc si le contenu du Registre est modifié par le **`__asm`** bloc. Enfin, certaines optimisations au niveau de la fonction seront affectées par l'inclusion du langage assembleur dans une fonction.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
