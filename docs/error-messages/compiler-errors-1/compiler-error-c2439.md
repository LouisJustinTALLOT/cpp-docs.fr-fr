---
title: Erreur du compilateur C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205359"
---
# <a name="compiler-error-c2439"></a>Erreur du compilateur C2439

'identificateur' : le membre n’a pas pu être initialisé

Un membre de classe, de structure ou d’Union ne peut pas être initialisé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Tentative d’initialisation d’une classe ou d’une structure de base indirecte.

1. Tentative d’initialisation d’un membre hérité d’une classe ou d’une structure. Un membre hérité doit être initialisé par le constructeur de la classe ou de la structure.
