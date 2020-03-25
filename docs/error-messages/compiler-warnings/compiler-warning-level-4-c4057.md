---
title: Avertissement du compilateur (niveau 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 45d2db56a7b0fc871de60743954012faf0f5c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185384"
---
# <a name="compiler-warning-level-4-c4057"></a>Avertissement du compilateur (niveau 4) C4057

'opérateur' : 'identificateur1' diffère de 'identificateur2' dans l’indirection vers des types de base légèrement différents

Deux expressions de pointeur font référence à des types de base différents. Les expressions sont utilisées sans conversion.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Mélange de types signés et non signés.

1. Mélange de types **short** et **long** .
