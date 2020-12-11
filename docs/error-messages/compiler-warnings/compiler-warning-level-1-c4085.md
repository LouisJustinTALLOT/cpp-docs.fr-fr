---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4085'
title: Avertissement du compilateur (niveau 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: 81a752e1497f0b65e99de53b14879220b58678ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155434"
---
# <a name="compiler-warning-level-1-c4085"></a>Avertissement du compilateur (niveau 1) C4085

le paramètre pragma attendu doit être 'on' ou 'off'

Le pragma exige un paramètre **on** ou **off** . Le pragma est ignoré.

L’exemple suivant génère l’avertissement C4085 :

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```
