---
title: once_flag, structure
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 004a5545e2eccab83b0846e2ae30b88c8431c99d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371436"
---
# <a name="onceflag-structure"></a>once_flag, structure

Représente un **struct** qui est utilisé avec la fonction de modèle [call_once](../standard-library/mutex-functions.md#call_once) pour vous assurer que l’initialisation le code est appelé une seule fois, même en présence de plusieurs threads d’exécution.

## <a name="syntax"></a>Syntaxe

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>Notes

Le `once_flag` **struct** possède uniquement un constructeur par défaut.

Les objets de type `once_flag` peuvent être créés, mais ils ne peuvent pas être copiés.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
