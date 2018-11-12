---
title: Avertissement du compilateur (niveau 3) C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: 4d433ff7d6b323fcb8508872d4e755f893a50f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571871"
---
# <a name="compiler-warning-level-3-c4023"></a>Avertissement du compilateur (niveau 3) C4023

'symbole' : pointeur based passé à une fonction non prototypée : paramètre nombre

Passer un pointeur based à une fonction non prototypée entraîne la normalisation du pointeur, avec des résultats imprévisibles.

Vous pouvez résoudre cet avertissement en utilisant des fonctions prototypées auxquelles sont passées des pointeurs based.