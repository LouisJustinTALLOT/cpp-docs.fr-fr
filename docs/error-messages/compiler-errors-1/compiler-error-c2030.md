---
title: Erreur du compilateur C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208030"
---
# <a name="compiler-error-c2030"></a>Erreur du compilateur C2030

un destructeur avec l'accessibilité 'protected private' ne peut pas être membre d'une classe déclarée 'sealed'

Une classe Windows Runtime déclarée comme `sealed` ne peut pas avoir un destructeur privé protégé. Seuls des destructeurs virtuels publics et non virtuels privés sont autorisés sur les types sealed. Pour plus d’informations, consultez [Classes et structures de référence](../../cppcx/ref-classes-and-structs-c-cx.md).

Pour corriger cette erreur, modifiez l'accessibilité du destructeur.
