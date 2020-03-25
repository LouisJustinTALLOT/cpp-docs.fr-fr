---
title: Erreur du compilateur C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: a3e2268bfc5597668e8689d093a0c2bb7f18e037
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207283"
---
# <a name="compiler-error-c2129"></a>Erreur du compilateur C2129

fonction static’Function’déclarée mais non définie

Une référence anticipée est apportée à une fonction `static` qui n’est jamais définie.

Une fonction de `static` doit être définie dans la portée du fichier. Si la fonction est définie dans un autre fichier, elle doit être déclarée `extern`.
