---
title: Erreur du compilateur C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: e4661119680dff34dfaa43fb9ce71bf97150a8bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222490"
---
# <a name="compiler-error-c3297"></a>Erreur du compilateur C3297

'constraint_2' : impossible d’utiliser 'constraint_1' en tant que contrainte, car 'constraint_1' a la contrainte de valeur

Les classes de valeur sont sealed. Si une contrainte est une classe de valeur, une autre contrainte ne peut jamais dériver de celle-ci.

Pour plus d’informations, consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3297 :

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```