---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4057'
title: Avertissement du compilateur (niveau 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 0b5da5c4768f4101b7b1780b5d0518ed723c5225
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262085"
---
# <a name="compiler-warning-level-4-c4057"></a>Avertissement du compilateur (niveau 4) C4057

'opérateur' : 'identificateur1' diffère de 'identificateur2' dans l’indirection vers des types de base légèrement différents

Deux expressions de pointeur font référence à des types de base différents. Les expressions sont utilisées sans conversion.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Mélange de types signés et non signés.

1. Combinaison **`short`** de **`long`** types et.
