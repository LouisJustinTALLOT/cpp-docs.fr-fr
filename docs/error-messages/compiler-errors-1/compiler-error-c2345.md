---
description: 'En savoir plus sur : erreur du compilateur C2345'
title: Erreur du compilateur C2345
ms.date: 11/04/2016
f1_keywords:
- C2345
helpviewer_keywords:
- C2345
ms.assetid: e1cc88b0-0223-4d07-975b-fa99956a82bd
ms.openlocfilehash: 021c792a93fa27712087908ab30e1ddec84d08fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298407"
---
# <a name="compiler-error-c2345"></a>Erreur du compilateur C2345

align(valeur) : valeur d’alignement non conforme

Vous avez passé une valeur au mot clé [align](../../cpp/align-cpp.md) qui n’est pas comprise dans la plage autorisée.

L’exemple suivant génère l’erreur C2345 :

```cpp
// C2345.cpp
// compile with: /c
__declspec(align(0)) int a;   // C2345
__declspec(align(1)) int a;   // OK
```
