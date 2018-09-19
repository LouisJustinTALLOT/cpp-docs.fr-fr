---
title: Erreur du compilateur C2978 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2978
dev_langs:
- C++
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40d7569a250812d6807c4723366b88e2f290be85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045183"
---
# <a name="compiler-error-c2978"></a>Erreur du compilateur C2978

erreur de syntaxe : 'mot_clé1' ou 'mot_clé2' attendu ; type 'mot_clé3' trouvé ; les paramètres sans type ne sont pas pris en charge dans les génériques

Une classe générique a été déclarée incorrectement. Consultez [génériques](../../windows/generics-cpp-component-extensions.md)pour plus d’informations.

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