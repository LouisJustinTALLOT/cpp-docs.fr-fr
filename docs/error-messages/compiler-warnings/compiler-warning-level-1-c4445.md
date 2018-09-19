---
title: Compilateur avertissement (niveau 1) C4445 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4445
dev_langs:
- C++
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80b3e13f0f7271a38d71c65efa65f104e44aa475
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079945"
---
# <a name="compiler-warning-level-1-c4445"></a>Avertissement du compilateur (niveau 1) C4445

'fonction' : dans un type WinRT ou managé, une méthode virtuelle ne peut pas être privée

Si une fonction virtuelle est privée, un type dérivé ne peut pas y accéder. Pour corriger cette erreur, modifiez l'accessibilité de la fonction membre virtuelle pour qu'elle soit protégée ou publique.