---
title: Erreur du compilateur C2414 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2414
dev_langs:
- C++
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 642cb00605ed13146288edf5d39cb5d0c14c6e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089916"
---
# <a name="compiler-error-c2414"></a>Erreur du compilateur C2414

nombre non conforme d’opérandes

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. L’opcode ne prend pas en charge le nombre d’opérandes utilisé. Vérifier un manuel de référence de langage assembleur pour déterminer le nombre correct d’opérandes.

1. Un processeur plus récent prend en charge l’instruction avec un nombre différent d’opérandes. Ajuster la [/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md) permet d’utiliser le processeur le plus récent.