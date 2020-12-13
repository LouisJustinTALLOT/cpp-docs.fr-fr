---
description: 'En savoir plus sur : erreur du compilateur C3118'
title: Erreur du compilateur C3118
ms.date: 11/04/2016
f1_keywords:
- C3118
helpviewer_keywords:
- C3118
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
ms.openlocfilehash: cc6d9c446603adaa314480f8f18ae8bd2c168277
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151097"
---
# <a name="compiler-error-c3118"></a>Erreur du compilateur C3118

'interface' : les interfaces ne prennent pas en charge l’héritage virtuel

Vous avez tenté d’hériter virtuellement d’une interface. Par exemple :

```cpp
// C3118.cpp
__interface I1 {
};

__interface I2 : virtual I1 {   // C3118
};
```

génère cette erreur.
