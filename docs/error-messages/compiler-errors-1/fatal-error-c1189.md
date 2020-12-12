---
description: 'En savoir plus sur : erreur irrécupérable C1189'
title: Erreur irrécupérable C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 4e71903c6567aedf85de81db59b66e45684d8507
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123589"
---
# <a name="fatal-error-c1189"></a>Erreur irrécupérable C1189

> **\# erreur :** *message d’erreur fourni* par l’utilisateur

## <a name="remarks"></a>Notes

C1189 est généré par la `#error` directive. Le développeur qui code la directive spécifie le texte du message d’erreur. Pour plus d’informations, consultez [#error directive (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C1189. Dans l’exemple, le développeur émet un message d’erreur personnalisé, car l' `_WIN32` identificateur n’est pas défini :

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Voir aussi

[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
