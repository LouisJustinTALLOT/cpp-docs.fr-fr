---
description: 'En savoir plus sur : erreur du compilateur C2978'
title: Erreur du compilateur C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 7f39b6d7b01790bd8865c4e176ff8ed865756edb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281819"
---
# <a name="compiler-error-c2978"></a>Erreur du compilateur C2978

erreur de syntaxe : 'mot_clé1' ou 'mot_clé2' attendu ; type 'mot_clé3' trouvé ; les paramètres sans type ne sont pas pris en charge dans les génériques

Une classe générique a été déclarée incorrectement. Pour plus d’informations, consultez [génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2978.

```cpp
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```
