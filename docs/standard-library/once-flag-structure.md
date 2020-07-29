---
title: once_flag, structure
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 55c3f90f72857a4e4cd3f9075ce5bae10e14d218
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202725"
---
# <a name="once_flag-structure"></a>once_flag, structure

Représente un **`struct`** utilisé avec la fonction de modèle [call_once](../standard-library/mutex-functions.md#call_once) pour garantir que le code d’initialisation est appelé une seule fois, même en présence de plusieurs threads d’exécution.

## <a name="syntax"></a>Syntaxe

struct once_flag {constexpr once_flag () noexcept ;};

## <a name="remarks"></a>Notes

`once_flag` **`struct`** A uniquement un constructeur par défaut.

Les objets de type `once_flag` peuvent être créés, mais ils ne peuvent pas être copiés.

## <a name="requirements"></a>Spécifications

**En-tête :**\<mutex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
