---
title: Compilateur avertissement (niveau 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: a4958bb446b5f7e80ef2eef92b52a0f86cf6a134
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479402"
---
# <a name="compiler-warning-level-1-c4049"></a>Compilateur avertissement (niveau 1) C4049

limite du compilateur : arrêt de l’émission de numéros de ligne

Le fichier contient plus de 16 777 215 (2<sup>24</sup>-1) lignes sources. Le compilateur arrête la numérotation à 16 777 215.

Pour le code après la ligne 16 777 215 :

- L’image ne contient aucune information de débogage pour les numéros de ligne.

- Certains diagnostics peuvent être signalés avec des numéros de ligne.

- listes .asm (/ FA) peut avoir des numéros de ligne.