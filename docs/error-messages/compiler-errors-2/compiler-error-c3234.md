---
description: 'En savoir plus sur : erreur du compilateur C3234'
title: Erreur du compilateur C3234
ms.date: 11/04/2016
f1_keywords:
- C3234
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
ms.openlocfilehash: 8e43b4ae7151d3be32ffc18ccec9995de67c21cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311966"
---
# <a name="compiler-error-c3234"></a>Erreur du compilateur C3234

une classe générique ne peut pas dériver d'un paramètre de type générique

Une classe générique ne peut pas hériter d’un paramètre de type générique.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3234.

```cpp
// C3234.cpp
// compile with: /clr /c
generic <class T>
public ref class C : T {};   // C3234
// try the following line instead
// public ref class C {};
```
