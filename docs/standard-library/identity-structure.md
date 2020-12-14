---
description: 'En savoir plus sur : structure d’identité'
title: identity, structure
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 753a3b697eb2a77dd102f681403fd23d7062cb36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231756"
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

*gauche*\
Valeur à identifier.

## <a name="remarks"></a>Notes

La classe contient la définition de type public `type`, qui est la même que le paramètre de modèle Type. Elle est utilisée conjointement avec la fonction de modèle [forward](../standard-library/utility-functions.md#forward) pour s’assurer qu’un paramètre de fonction a le type souhaité.

Pour la compatibilité avec le code plus ancien, la classe définit également la fonction d’identité `operator()` qui retourne son argument *Left*.
