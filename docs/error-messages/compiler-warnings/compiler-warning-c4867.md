---
title: Avertissement du compilateur C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: e093d262bc26cf0acfbb181d621fffc1aa391ee9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626588"
---
# <a name="compiler-warning-c4867"></a>Avertissement du compilateur C4867

'fonction' : liste d’arguments manquante dans l’appel de fonction ; Utilisez’Call’pour créer un pointeur vers un membre

Un pointeur vers une fonction membre a été initialisé de manière incorrecte.

Cet avertissement peut être généré à la suite du travail de conformité du compilateur pour Visual Studio 2005 : conformité de pointeur vers membre améliorée.  Le code compilé avant Visual Studio 2005 génère désormais C4867.

Cet avertissement est toujours émis en tant qu’erreur. Pour désactiver cet avertissement, utilisez le pragma [warning](../../preprocessor/warning.md) . Pour plus d’informations sur C4867 et MFC/ATL, consultez [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4867.

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```