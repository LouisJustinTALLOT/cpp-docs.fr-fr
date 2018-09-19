---
title: Erreur du compilateur C3174 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3174
dev_langs:
- C++
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca73c1fa16f2cc8b25f355705c7f0a72916158d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105184"
---
# <a name="compiler-error-c3174"></a>Erreur du compilateur C3174

attribut de module n’a pas été spécifié.

Un programme qui utilise des attributs Visual C++ ne pas également utiliser le [module](../../windows/module-cpp.md) attribut, qui est obligatoire dans tout programme qui utilise des attributs.

L’exemple suivant génère l’erreur C3174 :

```
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```