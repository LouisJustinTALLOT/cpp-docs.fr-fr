---
title: Avertissement du compilateur (niveau 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176310"
---
# <a name="compiler-warning-level-1-c4124"></a>Avertissement du compilateur (niveau 1) C4124

__fastcall avec la vérification de la pile est inefficace

Le mot clé `__fastcall` a été utilisé avec la vérification de la pile activée.

La Convention de `__fastcall` génère du code plus rapide, mais la vérification de pile entraîne un code plus lent. Quand vous utilisez `__fastcall`, désactivez la vérification de la pile avec le pragma **check_stack** ou/GS.

Cet avertissement est émis uniquement pour la première fonction déclarée dans ces conditions.
