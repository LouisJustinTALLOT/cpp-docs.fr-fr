---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4659'
title: Avertissement du compilateur (niveau 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 05ec1e088e00b184ba083b6b197afc6041707449
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318809"
---
# <a name="compiler-warning-level-1-c4659"></a>Avertissement du compilateur (niveau 1) C4659

\#pragma’pragma' : l’utilisation du segment réservé’segment’a un comportement indéfini, utilisez #pragma commentaire (éditeur de liens,...)

L’option. drectve a été utilisée pour passer une option à l’éditeur de liens. Utilisez plutôt pragma [Comment](../../preprocessor/comment-c-cpp.md) pour passer une option de l’éditeur de liens.

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
