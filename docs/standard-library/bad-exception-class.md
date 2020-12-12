---
description: 'En savoir plus sur : classe bad_exception'
title: bad_exception, classe
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 6b47facc751e1f16e033f26be284db1287e79ea8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321610"
---
# <a name="bad_exception-class"></a>bad_exception, classe

La classe décrit une exception pouvant être levée à partir d’un gestionnaire d’exceptions inattendues.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>Notes

[unexpected](../standard-library/exception-functions.md#unexpected) lève un `bad_exception` au lieu de terminer ou d’appeler une autre fonction spécifiée par [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` est inclus dans la liste d’exceptions levées d’une fonction.

La valeur retournée par `what` est une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

Pour obtenir la liste des membres hérités par la classe `bad_exception`, consultez [exception, classe](../standard-library/exception-class.md).

## <a name="example"></a>Exemple

Consultez [set_unexpected](../standard-library/exception-functions.md#set_unexpected) pour obtenir un exemple d’utilisation de la fonction [unexpected](../standard-library/exception-functions.md#unexpected) levant un `bad_exception`.
