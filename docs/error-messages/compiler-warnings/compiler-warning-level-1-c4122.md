---
title: Avertissement du compilateur (niveau 1) C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: a01899de643a1f10f2211a67025fd3f46c546b8a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176323"
---
# <a name="compiler-warning-level-1-c4122"></a>Avertissement du compilateur (niveau 1) C4122

'function' : alloc_text ne peut s’appliquer qu’aux fonctions avec liaison C

Le pragma **alloc_text** s’applique uniquement aux fonctions déclarées avec **extern c**. Il ne peut pas être utilisé avec des fonctions C++ externes.

Le pragma est ignoré.
