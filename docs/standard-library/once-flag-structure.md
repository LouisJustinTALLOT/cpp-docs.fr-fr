---
title: once_flag, structure
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455204"
---
# <a name="onceflag-structure"></a>once_flag, structure

Représente un **struct** utilisé avec la fonction de modèle [call_once](../standard-library/mutex-functions.md#call_once) pour garantir que le code d’initialisation est appelé une seule fois, même en présence de plusieurs threads d’exécution.

## <a name="syntax"></a>Syntaxe

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>Notes

La `once_flag` **structure** a uniquement un constructeur par défaut.

Les objets de type `once_flag` peuvent être créés, mais ils ne peuvent pas être copiés.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> mutex

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
