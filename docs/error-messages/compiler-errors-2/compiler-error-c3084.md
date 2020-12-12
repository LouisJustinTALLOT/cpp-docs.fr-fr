---
description: 'En savoir plus sur : erreur du compilateur C3084'
title: Erreur du compilateur C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 8603930e9087f1e407d5e8df65078604836b9a16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320117"
---
# <a name="compiler-error-c3084"></a>Erreur du compilateur C3084

'function' : un finaliseur/destructeur ne peut pas avoir la valeur 'keyword'

Un finaliseur ou un destructeur n’a pas été correctement déclaré.

Par exemple, un destructeur ne doit pas être marqué comme sealed.  Le destructeur sera inaccessible aux types dérivés.  Pour plus d’informations, consultez substitutions et destructeurs [explicites](../../extensions/explicit-overrides-cpp-component-extensions.md) [et finaliseurs dans Guide pratique pour définir et consommer des classes et des structs (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3084.

```cpp
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```
