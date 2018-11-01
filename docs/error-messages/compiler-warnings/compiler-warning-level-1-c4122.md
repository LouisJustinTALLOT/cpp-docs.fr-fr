---
title: Avertissement du compilateur (niveau 1) C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: bb5016bbf323057822c89a74001c75ab1855542c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490335"
---
# <a name="compiler-warning-level-1-c4122"></a>Avertissement du compilateur (niveau 1) C4122

'function' : alloc_text ne peut s’appliquer qu’aux fonctions avec liaison C

Le pragma **alloc_text** s’applique uniquement aux fonctions déclarées avec **extern c**. Il ne peut pas être utilisé avec des fonctions C++ externes.

Le pragma est ignoré.