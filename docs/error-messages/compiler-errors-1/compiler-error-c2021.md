---
title: Erreur du compilateur C2021 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31169c59ba9731d8eda52f22644294b8bb680bf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101985"
---
# <a name="compiler-error-c2021"></a>Erreur du compilateur C2021

valeur d’exposant attendue, non 'caractère'

Caractère utilisé comme exposant d’une constante à virgule flottante n’est pas un nombre valide. Veillez à utiliser un exposant qui se trouve dans la plage.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2021 :

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Exemple

Solution possible :

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```