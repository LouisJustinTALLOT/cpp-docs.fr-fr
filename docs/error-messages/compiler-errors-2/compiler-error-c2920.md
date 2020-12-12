---
description: 'En savoir plus sur : erreur du compilateur C2920'
title: Erreur du compilateur C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 08c11832fc2241fb8fbebf7bda56db29bf181022
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270327"
---
# <a name="compiler-error-c2920"></a>Erreur du compilateur C2920

redéfinition : 'classe' : la classe de modèle ou générique a déjà été déclarée comme 'type'

Une classe générique ou de modèle possède plusieurs déclarations, qui ne sont pas équivalentes. Pour corriger cette erreur, utilisez des noms différents pour des types différents ou supprimez la redéfinition du nom de type.

L'exemple suivant génère l'erreur C2920 et montre comment la corriger :

```cpp
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

L'erreur C2920 peut également se produire lors de l'utilisation de génériques :

```cpp
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```
