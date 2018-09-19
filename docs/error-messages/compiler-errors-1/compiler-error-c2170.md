---
title: Erreur du compilateur C2170 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2170
dev_langs:
- C++
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b75d4c54bc6ec24cb182f3b6fb37ff4b8cd1ddfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055726"
---
# <a name="compiler-error-c2170"></a>Erreur du compilateur C2170

'identificateur' : non déclaré comme fonction, ne peut pas être intrinsèque

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Pragma `intrinsic` est utilisé pour un élément autre qu’une fonction.

1. Pragma `intrinsic` est utilisé pour une fonction sans forme intrinsèque.