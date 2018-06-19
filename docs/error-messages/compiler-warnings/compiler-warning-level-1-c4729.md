---
title: Compilateur avertissement (niveau 1) C4729 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02ccbb80a44123498a231c1909c9c2c6fca72a24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281740"
---
# <a name="compiler-warning-level-1-c4729"></a>Avertissement du compilateur (niveau 1) C4729
fonction trop importante pour les avertissements bas‚s sur les graphes de flux  
  
 Cet avertissement est généré quand une fonction est trop grande pour être compilée avec un contrôle fiable des situations qui génèrent un avertissement. Cet avertissement n’est généré que quand l’option du compilateur [/Od](../../build/reference/od-disable-debug.md) est utilisée.  
  
 Pour remédier à cet avertissement, fractionnez la fonction en fonctions plus petites.