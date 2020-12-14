---
description: 'En savoir plus sur : erreur du compilateur C3197'
title: Erreur du compilateur C3197
ms.date: 11/04/2016
f1_keywords:
- C3197
helpviewer_keywords:
- C3197
ms.assetid: 4e385c3b-222e-425c-9612-46e83ed41650
ms.openlocfilehash: f03792a2dd5120ed2b4a05b2110186d5c985e502
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203755"
---
# <a name="compiler-error-c3197"></a>Erreur du compilateur C3197

'keyword' : ne peut être utilisé que dans les définitions

Un mot clé a été utilisé dans une déclaration, mais n’est valide que dans une définition.

L’exemple suivant génère l’C3197 :

```cpp
// C3197.cpp
// compile with: /clr /c
ref struct R abstract;   // C3197
ref struct R abstract {};   // OK

public ref class MyObject;   // C3197
ref class MyObject;   // OK
public ref class MyObject {};   // OK
```
