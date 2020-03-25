---
title: Avertissement du compilateur (niveau 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185982"
---
# <a name="compiler-warning-level-1-c4612"></a>Avertissement du compilateur (niveau 1) C4612

> erreur dans le nom de fichier Include

## <a name="remarks"></a>Notes

Cet avertissement se produit avec **#pragma include_alias** quand un nom de fichier est incorrect ou manquant.

Les arguments de l’instruction **#pragma include_alias** peuvent utiliser le format de guillemet ("*nom_fichier*") ou le format de crochet angulaire (\<*nom de fichier*>), mais les deux doivent utiliser le même formulaire.

## <a name="example"></a>Exemple

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
