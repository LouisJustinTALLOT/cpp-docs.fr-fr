---
title: time_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: 85565dc0c0ec904551eb8dd981cfacc9a2e1f256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460038"
---
# <a name="timebase-class"></a>time_base, classe

La classe sert de classe de base pour les facettes de la classe de modèle time_get, en définissant `dateorder` uniquement le type énuméré et plusieurs constantes de ce type.

## <a name="syntax"></a>Syntaxe

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>Notes

Chaque constante caractérise une manière différente d’ordonner les composants d’une date. Les constantes sont :

- `no_order`ne spécifie aucun ordre particulier.

- `dmy`Spécifie le jour, le mois et l’année de la commande, comme dans 2 décembre 1979.

- `mdy`Spécifie l’ordre mois, jour, année, comme le 2 décembre 1979.

- `ymd`Spécifie l’année, le mois, le jour de la commande, comme dans 1979/12/2.

- `ydm`Spécifie l’année, le jour et le mois de la commande, comme dans 1979: 2 déc.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
