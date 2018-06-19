---
title: Erreur irrécupérable C1189 | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199792"
---
# <a name="fatal-error-c1189"></a>Erreur irrécupérable C1189

> **\#Erreur :** *message d’erreur fourni par l’utilisateur*

## <a name="remarks"></a>Notes

L’erreur C1189 est générée par le `#error` la directive. Le développeur qui code la directive spécifie le texte du message d’erreur. Pour plus d’informations, consultez [#error Directive (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C1189. Dans l’exemple, le développeur émet un message d’erreur personnalisé, car le `_WIN32` identificateur n’est pas défini :

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Voir aussi

[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)