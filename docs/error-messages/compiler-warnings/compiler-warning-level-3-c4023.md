---
title: Avertissement du compilateur (niveau 3) C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: ed24c48b4054aacf673b031ebc05409a5c3e91dd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161605"
---
# <a name="compiler-warning-level-3-c4023"></a>Avertissement du compilateur (niveau 3) C4023

'symbole' : pointeur based passé à une fonction non prototypée : paramètre nombre

Passer un pointeur based à une fonction non prototypée entraîne la normalisation du pointeur, avec des résultats imprévisibles.

Vous pouvez résoudre cet avertissement en utilisant des fonctions prototypées auxquelles sont passées des pointeurs based.
