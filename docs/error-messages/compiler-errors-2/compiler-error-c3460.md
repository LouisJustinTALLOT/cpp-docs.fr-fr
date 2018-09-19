---
title: Erreur du compilateur C3460 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3460
dev_langs:
- C++
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64854420acf0b95cbb7ced8e4d4260735b07037e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109988"
---
# <a name="compiler-error-c3460"></a>Erreur du compilateur C3460

'type' : seul un type défini par l’utilisateur peut être transféré

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un composant.

```
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3460.

```
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```