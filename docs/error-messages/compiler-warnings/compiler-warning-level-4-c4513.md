---
title: Avertissement du compilateur (niveau 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: cbde035a988e5f6ac64303b2ed159b885ece8684
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520075"
---
# <a name="compiler-warning-level-4-c4513"></a>Avertissement du compilateur (niveau 4) C4513

'class' : destructeur n’a pas pu être généré.

Le compilateur ne peut pas générer un destructeur par défaut pour la classe donnée ; aucun destructeur a été créé. Le destructeur est dans une classe de base qui n’est pas accessible à la classe dérivée. Si la classe de base a un destructeur privé, rendre publique ou protégée.