---
description: 'En savoir plus sur : erreur du compilateur C3152'
title: Erreur du compilateur C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: b7e98535003a03ec5ac8b06d23b105d3727ff605
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322060"
---
# <a name="compiler-error-c3152"></a>Erreur du compilateur C3152

'construction' : 'mot clé' ne peut s'appliquer qu'à une classe, une structure ou une fonction membre virtuelle

Certains mots clés ne peuvent être appliqués qu'à une classe C++.

L'exemple suivant génère l'erreur C3152 et montre comment la corriger :

```cpp
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
