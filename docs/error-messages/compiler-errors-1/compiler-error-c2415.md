---
title: Erreur du compilateur C2415 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd889880997828396521ddba638bb606552e7d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112575"
---
# <a name="compiler-error-c2415"></a>Erreur du compilateur C2415

type d’opérande incorrect

L’opcode n’utilise pas les opérandes de ce type.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. L’opcode ne prend pas en charge le nombre d’opérandes utilisé. Vérifier un manuel de référence de langage assembleur pour déterminer le nombre correct d’opérandes.

1. Un processeur plus récent prend en charge l’instruction avec des types supplémentaires. Ajuster la [/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md) permet d’utiliser le processeur le plus récent.