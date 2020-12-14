---
description: 'En savoir plus sur : erreur du compilateur C2439'
title: Erreur du compilateur C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 6493fb634581646c20a8d856658fe728ae27364c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189806"
---
# <a name="compiler-error-c2439"></a>Erreur du compilateur C2439

'identificateur' : le membre n’a pas pu être initialisé

Un membre de classe, de structure ou d’Union ne peut pas être initialisé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Tentative d’initialisation d’une classe ou d’une structure de base indirecte.

1. Tentative d’initialisation d’un membre hérité d’une classe ou d’une structure. Un membre hérité doit être initialisé par le constructeur de la classe ou de la structure.
