---
title: Erreur du compilateur C3550 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c22d7e371fda7a229b541f78d4385f2943ee54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047783"
---
# <a name="compiler-error-c3550"></a>Erreur du compilateur C3550

'decltype(auto)' simple est le seul autorisé dans ce contexte

Si `decltype(auto)` est utilisé comme espace réservé pour le type de retour d'une fonction, il doit être utilisé par lui-même. Il ne peut pas être utilisé dans le cadre d'une déclaration de pointeur (`decltype(auto*)`), d'une déclaration de référence (`decltype(auto&)`) ni de toute autre qualification de ce genre.

## <a name="see-also"></a>Voir aussi

[auto](../../cpp/auto-cpp.md)