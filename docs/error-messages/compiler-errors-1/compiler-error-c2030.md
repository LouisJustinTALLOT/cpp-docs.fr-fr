---
title: Erreur du compilateur C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: f9090e098d7f523bf7bc12b7fa4d9312f6ca5466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212902"
---
# <a name="compiler-error-c2030"></a>Erreur du compilateur C2030

un destructeur avec l'accessibilité 'protected private' ne peut pas être membre d'une classe déclarée 'sealed'

Une classe Windows Runtime déclarée comme **`sealed`** ne peut pas avoir de destructeur privé protégé. Seuls des destructeurs virtuels publics et non virtuels privés sont autorisés sur les types sealed. Pour plus d’informations, consultez [Classes et structures de référence](../../cppcx/ref-classes-and-structs-c-cx.md).

Pour corriger cette erreur, modifiez l'accessibilité du destructeur.
