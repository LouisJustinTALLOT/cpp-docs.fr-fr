---
description: 'En savoir plus sur : erreur du compilateur C2007'
title: Erreur du compilateur C2007
ms.date: 11/04/2016
f1_keywords:
- C2007
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
ms.openlocfilehash: fa2ad780269079ef081f22d2c222e106443200e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298485"
---
# <a name="compiler-error-c2007"></a>Erreur du compilateur C2007

\#définir la syntaxe

Aucun identificateur n’apparaît après un `#define` . Pour résoudre l’erreur, utilisez un identificateur.

L’exemple suivant génère l’C2007 :

```cpp
// C2007.cpp
#define   // C2007
```

Solution possible :

```cpp
// C2007b.cpp
// compile with: /c
#define true 1
```
