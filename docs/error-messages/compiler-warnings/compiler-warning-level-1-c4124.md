---
title: Compilateur avertissement (niveau 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582566"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilateur avertissement (niveau 1) C4124

__fastcall avec contrôle de pile est inefficace

Le `__fastcall` mot clé a été utilisé avec le contrôle de pile activé.

Le `__fastcall` convention génère du code plus rapide, mais le contrôle de pile provoque ralentit le code. Lorsque vous utilisez `__fastcall`, désactiver la vérification de la pile avec le **check_stack** pragma ou/GS.

Cet avertissement est émis uniquement pour la première fonction déclarée dans ces conditions.