---
title: Erreur du compilateur C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: f267d195ba851a9d585961848062fa271168aeb8
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743332"
---
# <a name="compiler-error-c3462"></a>Erreur du compilateur C3462

'type' : seul un type importé peut être transféré

L’attribut TypeForwardedTo doit être appliqué à un type dans les métadonnées référencées.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

L’exemple suivant génère l’erreur C3462.

```cpp
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
