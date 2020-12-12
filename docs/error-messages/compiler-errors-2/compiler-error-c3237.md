---
description: 'En savoir plus sur : erreur du compilateur C3237'
title: Erreur du compilateur C3237
ms.date: 11/04/2016
f1_keywords:
- C3237
helpviewer_keywords:
- C3237
ms.assetid: 690970c8-e13b-4ff3-96e3-5fd93c4d356b
ms.openlocfilehash: 4cfb42f7b8267623d085794822f2688c8798b2d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307481"
---
# <a name="compiler-error-c3237"></a>Erreur du compilateur C3237

'generic_class' : une classe générique ne peut pas être un attribut personnalisé

Les classes génériques ne peuvent pas être des attributs définis par l’utilisateur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3237.

```cpp
// C3237.cpp
// compile with: /clr /c
// C3237 expected
using namespace System;

generic <class T>
// Delete the following line to resolve.
[attribute(AttributeTargets::All, AllowMultiple=true)]
public ref class GR {};
```
