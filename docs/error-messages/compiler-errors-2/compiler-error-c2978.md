---
title: Erreur du compilateur C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: cf682bf14246754cca74a43dffc39761ff6125c1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780299"
---
# <a name="compiler-error-c2978"></a>Erreur du compilateur C2978

erreur de syntaxe : 'mot_clé1' ou 'mot_clé2' attendu ; type 'mot_clé3' trouvé ; les paramètres sans type ne sont pas pris en charge dans les génériques

Une classe générique a été déclarée incorrectement. Consultez [génériques](../../extensions/generics-cpp-component-extensions.md)pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2978.

```
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