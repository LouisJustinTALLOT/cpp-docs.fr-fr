---
title: once_flag, structure | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104333"
---
# <a name="onceflag-structure"></a>once_flag, structure

Représente un **struct** qui est utilisé avec la fonction de modèle [call_once](../standard-library/mutex-functions.md#call_once) pour vous assurer que l’initialisation le code est appelé une seule fois, même en présence de plusieurs threads d’exécution.

## <a name="syntax"></a>Syntaxe

struct once_flag {constexpr once_flag() noexcept ;} ;

## <a name="remarks"></a>Notes

Le `once_flag` **struct** possède uniquement un constructeur par défaut.

Les objets de type `once_flag` peuvent être créés, mais ils ne peuvent pas être copiés.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
