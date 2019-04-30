---
title: identity, structure
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 722eb9c0579d0c07765434127d0a7c43718fbc37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404995"
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
