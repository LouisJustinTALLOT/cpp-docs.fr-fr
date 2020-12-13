---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4612'
title: Avertissement du compilateur (niveau 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: 2844b54c592f5c4c4817cfec97d57c41fa2055b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341722"
---
# <a name="compiler-warning-level-1-c4612"></a>Avertissement du compilateur (niveau 1) C4612

> erreur dans le nom de fichier Include

## <a name="remarks"></a>Notes

Cet avertissement se produit avec **#pragma include_alias** quand un nom de fichier est incorrect ou manquant.

Les arguments de l’instruction **#pragma include_alias** peuvent utiliser le format de guillemet ("*nom_fichier*") ou le format de crochet angulaire ( \<*filename*> ), mais les deux doivent utiliser la même forme.

## <a name="example"></a>Exemple

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
