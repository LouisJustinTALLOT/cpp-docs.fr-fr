---
title: time_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: e790237e506aa32bafdb39938d841307bbc4d9c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593399"
---
# <a name="timebase-class"></a>time_base, classe

La classe sert de classe de base pour les facettes de modèle classe time_get, définissant simplement le type énuméré `dateorder` et plusieurs constantes de ce type.

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

- `no_order` ne spécifie aucun ordre particulier.

- `dmy` Spécifie l’ordre jour, mois, année, comme dans 2 décembre 1979.

- `mdy` Spécifie l’ordre mois, jour, année, comme dans le 2 décembre 1979.

- `ymd` Spécifie l’ordre année, mois, jour, comme dans 1979/12/2.

- `ydm` Spécifie l’ordre année, jour, mois, comme dans 1979:2 déc.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
