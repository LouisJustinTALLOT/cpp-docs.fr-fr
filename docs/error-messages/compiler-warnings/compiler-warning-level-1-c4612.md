---
title: Avertissement du compilateur (niveau 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406364"
---
# <a name="compiler-warning-level-1-c4612"></a>Avertissement du compilateur (niveau 1) C4612

> erreur dans le nom de fichier Include

## <a name="remarks"></a>Notes

Cet avertissement se produit avec **#pragma include_alias** quand un nom de fichier est incorrect ou manquant.

Les arguments de la **#pragma include_alias** instruction peut utiliser le formulaire de devis («*filename*») ou les crochets pointus (\<*filename*>), mais les deux doivent utiliser la même forme.

## <a name="example"></a>Exemple

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```