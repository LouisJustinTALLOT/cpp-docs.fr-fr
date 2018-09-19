---
title: Compilateur avertissement (niveau 1) C4420 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049746"
---
# <a name="compiler-warning-level-1-c4420"></a>Avertissement du compilateur (niveau 1) C4420

'opérateur' : opérateur non disponible, à l’aide de 'operator' à la place. vérification de l’exécution peut être compromise.

Cet avertissement est généré lorsque vous utilisez le [que /RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector, new et delete/vérification) et qu’aucune forme vecteur n’est trouvée. Dans ce cas, la forme non vecteur est utilisée.

Dans l’ordre pour que /RTCv fonctionne correctement, le compilateur doit toujours appeler la forme de vecteur de [nouveau](../../cpp/new-operator-cpp.md)/[supprimer](../../cpp/delete-operator-cpp.md) si la syntaxe vecteur a été utilisée.