---
title: Erreur du compilateur C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: 9cf414200dcfad8ae617e16e111bd26b19a315a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220429"
---
# <a name="compiler-error-c2129"></a>Erreur du compilateur C2129

fonction static’Function’déclarée mais non définie

Une référence anticipée est apportée à une **`static`** fonction qui n’est jamais définie.

Une **`static`** fonction doit être définie dans la portée du fichier. Si la fonction est définie dans un autre fichier, elle doit être déclarée **`extern`** .
