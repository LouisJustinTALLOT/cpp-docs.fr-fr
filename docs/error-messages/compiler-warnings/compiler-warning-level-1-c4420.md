---
title: Avertissement du compilateur (niveau 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662887"
---
# <a name="compiler-warning-level-1-c4420"></a>Avertissement du compilateur (niveau 1) C4420

'opérateur' : opérateur non disponible, à l’aide de 'operator' à la place. vérification de l’exécution peut être compromise.

Cet avertissement est généré lorsque vous utilisez le [que /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector, new et delete/vérification) et qu’aucune forme vecteur n’est trouvée. Dans ce cas, la forme non vecteur est utilisée.

Dans l’ordre pour que /RTCv fonctionne correctement, le compilateur doit toujours appeler la forme de vecteur de [nouveau](../../cpp/new-operator-cpp.md)/[supprimer](../../cpp/delete-operator-cpp.md) si la syntaxe vecteur a été utilisée.