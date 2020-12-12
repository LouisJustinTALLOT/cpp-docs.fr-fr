---
description: 'En savoir plus sur : erreur du compilateur C3388'
title: Erreur du compilateur C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 0acc4729b5b6de61476bc134b9ef7f79bb9e86e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285524"
---
# <a name="compiler-error-c3388"></a>Erreur du compilateur C3388

'type' : non autorisé en tant que contrainte, 'ref class' pris par défaut pour poursuivre l’analyse

Une contrainte a été spécifiée sur un type générique, mais la contrainte n’a pas été spécifiée correctement. Pour plus d’informations, consultez [contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3388.

```cpp
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```
