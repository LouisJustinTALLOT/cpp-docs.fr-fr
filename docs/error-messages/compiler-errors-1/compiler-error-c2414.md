---
description: 'En savoir plus sur : erreur du compilateur C2414'
title: Erreur du compilateur C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 5bf2d017ac0018fe092b5a003dee021dd13370b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340331"
---
# <a name="compiler-error-c2414"></a>Erreur du compilateur C2414

nombre d’opérandes non conforme

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. L’opcode ne prend pas en charge le nombre d’opérandes utilisés. Vérifiez un manuel de référence du langage assembleur pour déterminer le nombre correct d’opérandes.

1. Un processeur plus récent prend en charge l’instruction avec un nombre différent d’opérandes. Ajustez l’option [/Arch (architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md) pour utiliser le processeur ultérieur.
