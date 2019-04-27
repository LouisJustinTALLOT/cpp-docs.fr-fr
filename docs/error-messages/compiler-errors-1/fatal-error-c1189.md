---
title: Erreur irrécupérable C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 06d42316a0109ac063bba43cefebd9aab71c2e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229057"
---
# <a name="fatal-error-c1189"></a>Erreur irrécupérable C1189

> **\#Erreur :** *message d’erreur fourni par l’utilisateur*

## <a name="remarks"></a>Notes

L’erreur C1189 est générée par le `#error` directive. Le développeur qui code la directive spécifie le texte du message d’erreur. Pour plus d’informations, consultez [#error Directive (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

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