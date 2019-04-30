---
title: Erreur du compilateur C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400524"
---
# <a name="compiler-error-c2030"></a>Erreur du compilateur C2030

un destructeur avec l'accessibilité 'protected private' ne peut pas être membre d'une classe déclarée 'sealed'

Une classe Windows Runtime déclarée comme `sealed` ne peut pas avoir un destructeur privé protégé. Seuls des destructeurs virtuels publics et non virtuels privés sont autorisés sur les types sealed. Pour plus d’informations, consultez [classes et structs Ref](../../cppcx/ref-classes-and-structs-c-cx.md).

Pour corriger cette erreur, modifiez l'accessibilité du destructeur.