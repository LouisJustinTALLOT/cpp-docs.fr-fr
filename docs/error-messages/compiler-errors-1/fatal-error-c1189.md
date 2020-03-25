---
title: Erreur irrécupérable C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203630"
---
# <a name="fatal-error-c1189"></a>Erreur irrécupérable C1189

> **erreur\#:** *message d’erreur fourni* par l’utilisateur

## <a name="remarks"></a>Notes

C1189 est généré par la directive `#error`. Le développeur qui code la directive spécifie le texte du message d’erreur. Pour plus d’informations, consultez [#error directive (CC++/)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C1189. Dans l’exemple, le développeur émet un message d’erreur personnalisé, car l’identificateur de `_WIN32` n’est pas défini :

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Voir aussi

[#define, directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
