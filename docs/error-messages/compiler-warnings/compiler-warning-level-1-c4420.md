---
title: Avertissement du compilateur (niveau 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186788"
---
# <a name="compiler-warning-level-1-c4420"></a>Avertissement du compilateur (niveau 1) C4420

'operator' : opérateur non disponible, à l’aide de’operator’à la place ; la vérification au moment de l’exécution peut être compromise

Cet avertissement est généré quand vous utilisez [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (contrôle Vector New/Delete) et quand aucune forme vectorielle n’est trouvée. Dans ce cas, la forme non vectorielle est utilisée.

Pour que/RTCv fonctionne correctement, le compilateur doit toujours appeler la forme vectorielle de [new](../../cpp/new-operator-cpp.md)/[Delete](../../cpp/delete-operator-cpp.md) si la syntaxe du vecteur a été utilisée.
