---
title: Avertissement du compilateur (niveau 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: e78606f117251fa8ab1f08f2cef280a266309c32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185826"
---
# <a name="compiler-warning-level-1-c4729"></a>Avertissement du compilateur (niveau 1) C4729

fonction trop importante pour les avertissements bas‚s sur les graphes de flux

Cet avertissement est généré quand une fonction est trop grande pour être compilée avec un contrôle fiable des situations qui génèrent un avertissement. Cet avertissement n’est généré que quand l’option du compilateur [/Od](../../build/reference/od-disable-debug.md) est utilisée.

Pour remédier à cet avertissement, fractionnez la fonction en fonctions plus petites.
