---
description: 'En savoir plus sur : erreur du compilateur C2947'
title: Erreur du compilateur C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 5b1780d49f97bfab33e70a4dd7b1958b56c8df14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189481"
---
# <a name="compiler-error-c2947"></a>Erreur du compilateur C2947

' > 'attendu pour terminer la construction, 'syntaxe’trouvé

Une liste d’arguments générique ou de modèle n’a peut-être pas été correctement terminée.

Les C2947 peuvent également être générés par des erreurs de syntaxe.

L’exemple suivant génère l’C2947 :

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
