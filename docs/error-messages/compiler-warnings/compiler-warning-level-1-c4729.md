---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4729'
title: Avertissement du compilateur (niveau 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: de4da8a56f4b8c6788b972a154e8670c14c07d68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272212"
---
# <a name="compiler-warning-level-1-c4729"></a>Avertissement du compilateur (niveau 1) C4729

fonction trop importante pour les avertissements bas‚s sur les graphes de flux

Cet avertissement est généré quand une fonction est trop grande pour être compilée avec un contrôle fiable des situations qui génèrent un avertissement. Cet avertissement n’est généré que quand l’option du compilateur [/Od](../../build/reference/od-disable-debug.md) est utilisée.

Pour remédier à cet avertissement, fractionnez la fonction en fonctions plus petites.
