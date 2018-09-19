---
title: Compilateur avertissement (niveau 1) C4124 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090923"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilateur avertissement (niveau 1) C4124

__fastcall avec contrôle de pile est inefficace

Le `__fastcall` mot clé a été utilisé avec le contrôle de pile activé.

Le `__fastcall` convention génère du code plus rapide, mais le contrôle de pile provoque ralentit le code. Lorsque vous utilisez `__fastcall`, désactiver la vérification de la pile avec le **check_stack** pragma ou/GS.

Cet avertissement est émis uniquement pour la première fonction déclarée dans ces conditions.