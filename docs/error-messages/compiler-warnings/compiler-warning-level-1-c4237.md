---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4237'
title: Avertissement du compilateur (niveau 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: a83c40d54a5bd711fbc399ac4880a211f3cf9bd7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266245"
---
# <a name="compiler-warning-level-1-c4237"></a>Avertissement du compilateur (niveau 1) C4237

le mot clé’keyword’n’est pas encore pris en charge, mais réservé pour un usage ultérieur

Un mot clé dans la spécification C++ n’est pas implémenté dans le compilateur Microsoft C++, mais le mot clé n’est pas disponible en tant que symbole défini par l’utilisateur.

L’exemple suivant génère l’C4237 :

```cpp
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```
