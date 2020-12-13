---
description: 'En savoir plus sur : erreur du compilateur C2415'
title: Erreur du compilateur C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: 21bbeabe0a5eacea55d2a38ab515429e6468ba57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340344"
---
# <a name="compiler-error-c2415"></a>Erreur du compilateur C2415

type d’opérande incorrect

L’opcode n’utilise pas les opérandes de ce type.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. L’opcode ne prend pas en charge le nombre d’opérandes utilisés. Vérifiez un manuel de référence du langage assembleur pour déterminer le nombre correct d’opérandes.

1. Un processeur plus récent prend en charge l’instruction avec des types supplémentaires. Ajustez l’option [/Arch (architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md) pour utiliser le processeur ultérieur.
