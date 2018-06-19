---
title: Compilateur avertissement (niveau 1) C4420 | Documents Microsoft
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
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279108"
---
# <a name="compiler-warning-level-1-c4420"></a>Avertissement du compilateur (niveau 1) C4420
'opérateur' : opérateur non disponible, à l’aide de 'opérateur' à la place. vérification de l’exécution peut être compromise.  
  
 Cet avertissement est généré lorsque vous utilisez la [que /RTCv](../../build/reference/rtc-run-time-error-checks.md) (nouveau/supprimer la vérification de vecteur) et qu’aucune forme vecteur n’est trouvée. Dans ce cas, c’est la forme non vecteur qui est utilisée.  
  
 Dans l’ordre pour que /RTCv fonctionne correctement, le compilateur doit toujours appeler la forme vecteur de [nouveau](../../cpp/new-operator-cpp.md)/[supprimer](../../cpp/delete-operator-cpp.md) si la syntaxe vecteur a été utilisée.