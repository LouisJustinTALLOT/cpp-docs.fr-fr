---
title: Erreur du compilateur C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174677"
---
# <a name="compiler-error-c2170"></a>Erreur du compilateur C2170

'identificateur' : non déclaré comme fonction, ne peut pas être intrinsèque

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Pragma `intrinsic` est utilisé pour un élément autre qu’une fonction.

1. Pragma `intrinsic` est utilisé pour une fonction sans forme intrinsèque.