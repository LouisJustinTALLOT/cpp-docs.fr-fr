---
title: Erreur du compilateur C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 828e5bbca0b796864ec8b364ee69c18a3b5eea00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206948"
---
# <a name="compiler-error-c2170"></a>Erreur du compilateur C2170

'identifier' : non déclaré comme fonction, ne peut pas être intrinsèque

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Pragma `intrinsic` est utilisé pour un élément autre qu’une fonction.

1. Pragma `intrinsic` est utilisé pour une fonction sans forme intrinsèque.
