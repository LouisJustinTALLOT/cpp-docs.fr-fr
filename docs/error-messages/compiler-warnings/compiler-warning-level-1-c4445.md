---
title: Avertissement du compilateur (niveau 1) C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 2956758a6bdd074d7fc902c6ebac60af19e34b54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186762"
---
# <a name="compiler-warning-level-1-c4445"></a>Avertissement du compilateur (niveau 1) C4445

'fonction' : dans un type WinRT ou managé, une méthode virtuelle ne peut pas être privée

Si une fonction virtuelle est privée, un type dérivé ne peut pas y accéder. Pour corriger cette erreur, modifiez l'accessibilité de la fonction membre virtuelle pour qu'elle soit protégée ou publique.
