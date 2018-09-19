---
title: Erreur du compilateur C3462 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3462
dev_langs:
- C++
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eba9e063b60ff60403b8b4cc7136ccd1313ecc47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028036"
---
# <a name="compiler-error-c3462"></a>Erreur du compilateur C3462

'type' : seul un type importé peut être transféré

L’attribut TypeForwardedTo doit être appliqué à un type dans les métadonnées référencées.

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un composant.

```
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3462.

```
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```