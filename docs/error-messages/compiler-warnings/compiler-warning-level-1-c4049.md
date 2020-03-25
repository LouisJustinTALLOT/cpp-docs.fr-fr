---
title: Avertissement du compilateur (niveau 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164142"
---
# <a name="compiler-warning-level-1-c4049"></a>Avertissement du compilateur (niveau 1) C4049

limite du compilateur : arrêt de l’émission de numéros de ligne

Le fichier contient plus de 16 777 215 (2<sup>24</sup>-1) lignes sources. Le compilateur arrête la numérotation à 16 777 215.

Pour code après la ligne 16 777 215 :

- L’image ne contient aucune information de débogage pour les numéros de ligne.

- Certains Diagnostics peuvent être signalés avec des numéros de ligne incorrects.

- les listes. asm (/FAs) peuvent avoir des numéros de ligne incorrects.
