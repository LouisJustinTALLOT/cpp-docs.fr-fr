---
title: Erreur du compilateur C3747 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3747
dev_langs:
- C++
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1f657e6d3f64a4d8a2244ab2927a9a712c14b1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091671"
---
# <a name="compiler-error-c3747"></a>Erreur du compilateur C3747

paramètre de type par défaut manquant : paramètre param

Les paramètres génériques ou de modèle avec les valeurs par défaut ne peut pas être suivies dans la liste de paramètres paramètres qui n’ont pas de valeurs par défaut.

L’exemple suivant génère l’erreur C3747 :

```
// C3747.cpp
template <class T1 = int, class T2>   // C3747
struct MyStruct {};
```

Solution possible :

```
// C3747b.cpp
// compile with: /c
template <class T1, class T2 = int>
struct MyStruct {};
```