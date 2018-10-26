---
title: identity, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62acade082847386e065470f23ffe8374f82eb55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079192"
---
# <a name="identity-structure"></a>identity, structure

Struct qui fournit une définition de type comme paramètre de modèle.

## <a name="syntax"></a>Syntaxe

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*left*|Valeur à identifier.|

## <a name="remarks"></a>Notes

La classe contient la définition de type public `type`, qui est la même que le paramètre de modèle Type. Elle est utilisée conjointement avec la fonction de modèle [forward](../standard-library/utility-functions.md#forward) pour s’assurer qu’un paramètre de fonction a le type souhaité.

Pour la compatibilité avec le code plus ancien, la classe définit également la fonction identity `operator()` qui retourne son argument *gauche*.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<utility>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<utility>](../standard-library/utility.md)<br/>
