---
title: Erreur du compilateur C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311730"
---
# <a name="compiler-error-c2439"></a>Erreur du compilateur C2439

'identificateur' : membre n’a pas pu être initialisé.

Une classe, une structure ou un membre d’union ne peut pas être initialisé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Tente d’initialiser une classe de base indirecte ou une structure.

1. Tentative d’initialiser un membre hérité d’une classe ou structure. Un membre hérité doit être initialisé par le constructeur de la classe ou structure.