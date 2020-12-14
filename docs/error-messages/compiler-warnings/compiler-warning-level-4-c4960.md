---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4960'
title: Avertissement du compilateur (niveau 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 9a1e3d5390ffa4ffad101d1ea2c3164c04d12ca8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234577"
---
# <a name="compiler-warning-level-4-c4960"></a>Avertissement du compilateur (niveau 4) C4960

'function' est trop grand pour être profilé

Quand vous avez utilisé [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée avec une fonction comprenant plus de 65 535 instructions. Une fonction de cette taille n’est pas disponible pour les optimisations guidées par profil.

Pour résoudre cet avertissement, réduisez la taille de la fonction.
