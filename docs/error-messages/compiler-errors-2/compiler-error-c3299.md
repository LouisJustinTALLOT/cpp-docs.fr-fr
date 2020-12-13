---
description: 'En savoir plus sur : erreur du compilateur C3299'
title: Erreur du compilateur C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: ab86a675eb13b975943130802ae98679dbc1cbb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337413"
---
# <a name="compiler-error-c3299"></a>Erreur du compilateur C3299

'fonction_membre' : impossible de spécifier les contraintes, elles sont héritées de la méthode de base

Quand vous substituez une fonction membre générique, vous ne pouvez pas spécifier des clauses de contrainte (car la répétition de contraintes sous-entend que les contraintes ne sont pas héritées).

Les clauses de contrainte de la fonction générique que vous substituez seront héritées.

Pour plus d’informations, consultez [Contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3299 :

```cpp
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
