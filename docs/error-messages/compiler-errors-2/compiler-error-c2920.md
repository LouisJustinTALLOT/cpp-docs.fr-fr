---
title: Erreur du compilateur C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 28bbbd30bcb16e2ea5fc14fe0f48f86814ee13c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311668"
---
# <a name="compiler-error-c2920"></a>Erreur du compilateur C2920

redéfinition : 'classe' : la classe de modèle ou générique a déjà été déclarée comme 'type'

Une classe générique ou de modèle possède plusieurs déclarations, qui ne sont pas équivalentes. Pour corriger cette erreur, utilisez des noms différents pour des types différents ou supprimez la redéfinition du nom de type.

L'exemple suivant génère l'erreur C2920 et montre comment la corriger :

```
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

L'erreur C2920 peut également se produire lors de l'utilisation de génériques :

```
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```