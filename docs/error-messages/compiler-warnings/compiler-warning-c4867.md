---
title: Avertissement du compilateur C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 0fd5de46f713aed08508f8755c9e54c3ff46366b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447207"
---
# <a name="compiler-warning-c4867"></a>Avertissement du compilateur C4867

'fonction' : appel de fonction manquant de liste d’arguments ; Utilisez 'appel' pour créer un pointeur vers membre

Un pointeur vers la fonction membre a été initialisé correctement.

Cet avertissement peut être due à la mise en conformité du compilateur pour Visual Studio 2005 : conformité pointeur vers membre améliorée.  Le code compilé avant Visual Studio 2005 génère désormais C4867.

Cet avertissement est toujours émis en tant qu’erreur. Pour désactiver cet avertissement, utilisez le pragma [warning](../../preprocessor/warning.md) . Pour plus d’informations sur l’erreur C4867 et MFC/ATL, consultez [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4867.

```
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