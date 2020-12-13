---
description: 'En savoir plus sur : erreur du compilateur C2030'
title: Erreur du compilateur C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: b29996051a87f050e61c94b4134d046f52be6f09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175480"
---
# <a name="compiler-error-c2030"></a>Erreur du compilateur C2030

un destructeur avec l'accessibilité 'protected private' ne peut pas être membre d'une classe déclarée 'sealed'

Une classe Windows Runtime déclarée comme **`sealed`** ne peut pas avoir de destructeur privé protégé. Seuls des destructeurs virtuels publics et non virtuels privés sont autorisés sur les types sealed. Pour plus d’informations, consultez [Classes et structures de référence](../../cppcx/ref-classes-and-structs-c-cx.md).

Pour corriger cette erreur, modifiez l'accessibilité du destructeur.
