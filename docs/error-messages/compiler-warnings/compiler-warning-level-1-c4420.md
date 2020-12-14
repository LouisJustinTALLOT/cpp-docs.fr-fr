---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4420'
title: Avertissement du compilateur (niveau 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 2a92d7296bf5c38655182e5c0dd2c200d0ccf42d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311069"
---
# <a name="compiler-warning-level-1-c4420"></a>Avertissement du compilateur (niveau 1) C4420

'operator' : opérateur non disponible, à l’aide de’operator’à la place ; la vérification au moment de l’exécution peut être compromise

Cet avertissement est généré quand vous utilisez [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (contrôle Vector New/Delete) et quand aucune forme vectorielle n’est trouvée. Dans ce cas, la forme non vectorielle est utilisée.

Pour que/RTCv fonctionne correctement, le compilateur doit toujours appeler la forme vectorielle de [New](../../cpp/new-operator-cpp.md) / [Delete](../../cpp/delete-operator-cpp.md) si la syntaxe du vecteur a été utilisée.
