---
title: Erreur du compilateur C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 4ad48ea0bc09e098a41cb9aa969a08e9ead48f73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484827"
---
# <a name="compiler-error-c3299"></a>Erreur du compilateur C3299

'fonction_membre' : impossible de spécifier les contraintes, elles sont héritées de la méthode de base

Quand vous substituez une fonction membre générique, vous ne pouvez pas spécifier des clauses de contrainte (car la répétition de contraintes sous-entend que les contraintes ne sont pas héritées).

Les clauses de contrainte de la fonction générique que vous substituez seront héritées.

Pour plus d’informations, consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3299 :

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```