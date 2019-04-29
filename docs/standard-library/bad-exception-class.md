---
title: bad_exception, classe
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 94d1104b66fc6bd84e209caa23ce309cffd9fa85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377816"
---
# <a name="badexception-class"></a>bad_exception, classe

La classe décrit une exception pouvant être levée à partir d’un gestionnaire d’exceptions inattendues.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Notes

[unexpected](../standard-library/exception-functions.md#unexpected) lève un `bad_exception` au lieu de terminer ou d’appeler une autre fonction spécifiée par [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` est inclus dans la liste d’exceptions levées d’une fonction.

La valeur retournée par `what` est une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

Pour obtenir la liste des membres hérités par la classe `bad_exception`, consultez [exception, classe](../standard-library/exception-class.md).

## <a name="example"></a>Exemple

Consultez [set_unexpected](../standard-library/exception-functions.md#set_unexpected) pour obtenir un exemple d’utilisation de la fonction [unexpected](../standard-library/exception-functions.md#unexpected) levant un `bad_exception`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exception>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[exception, classe](../standard-library/exception-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
