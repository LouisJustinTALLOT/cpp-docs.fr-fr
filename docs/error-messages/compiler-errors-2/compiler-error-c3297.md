---
description: 'En savoir plus sur : erreur du compilateur C3297'
title: Erreur du compilateur C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 39cbdfe6bbc19341c904d6bae90a71595f388400
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144597"
---
# <a name="compiler-error-c3297"></a>Erreur du compilateur C3297

'constraint_2' : impossible d’utiliser 'constraint_1' en tant que contrainte, car 'constraint_1' a la contrainte de valeur

Les classes de valeur sont sealed. Si une contrainte est une classe de valeur, une autre contrainte ne peut jamais dériver de celle-ci.

Pour plus d’informations, consultez [Contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3297 :

```cpp
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```
