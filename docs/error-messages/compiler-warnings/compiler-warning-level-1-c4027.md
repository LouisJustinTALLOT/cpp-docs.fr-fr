---
description: En savoir plus sur l’avertissement du compilateur (niveau 1) C4027
title: Avertissement du compilateur (niveau 1) C4027
ms.date: 12/16/2020
f1_keywords:
- C4027
helpviewer_keywords:
- C4027
ms.openlocfilehash: 1489ca32211854bcf1ef55d1a4ac806ab1611f43
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645174"
---
# <a name="compiler-warning-level-1-c4027"></a>Avertissement du compilateur (niveau 1) C4027

> fonction déclarée sans liste de paramètres formels

La déclaration de fonction n’a pas de paramètres formels, mais il existe des paramètres formels dans la définition de fonction ou des paramètres réels dans un appel.

Le compilateur accepte, mais avertit, sur une ancienne déclaration anticipée de style C d’un nom de fonction sans liste de paramètres. Lors des appels ultérieurs à cette fonction, le compilateur suppose que la fonction prend des paramètres réels des types trouvés dans la définition de fonction ou l’appel. Nous vous recommandons de modifier votre déclaration de fonction pour qu’elle corresponde à la signature de la définition de fonction.
