---
title: Erreur du compilateur C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205619"
---
# <a name="compiler-error-c2415"></a>Erreur du compilateur C2415

type d’opérande incorrect

L’opcode n’utilise pas les opérandes de ce type.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. L’opcode ne prend pas en charge le nombre d’opérandes utilisés. Vérifiez un manuel de référence du langage assembleur pour déterminer le nombre correct d’opérandes.

1. Un processeur plus récent prend en charge l’instruction avec des types supplémentaires. Ajustez l’option [/Arch (architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md) pour utiliser le processeur ultérieur.
