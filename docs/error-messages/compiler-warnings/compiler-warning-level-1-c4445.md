---
title: Avertissement du compilateur (niveau 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 6c1b4f4ae4f60d0c4281e0bbcfc9ca2b58d81851
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611283"
---
# <a name="compiler-warning-level-1-c4445"></a>Avertissement du compilateur (niveau 1) C4445

'fonction' : dans un type WinRT ou managé, une méthode virtuelle ne peut pas être privée

Si une fonction virtuelle est privée, un type dérivé ne peut pas y accéder. Pour corriger cette erreur, modifiez l'accessibilité de la fonction membre virtuelle pour qu'elle soit protégée ou publique.