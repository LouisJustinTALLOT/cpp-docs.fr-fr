---
description: 'En savoir plus sur : classe time_base'
title: time_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: cad27546109cf8ed6d8314869a3306f238cc6528
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289567"
---
# <a name="time_base-class"></a>time_base, classe

La classe sert de classe de base pour les facettes de la time_get de modèle de classe, en définissant uniquement le type énuméré `dateorder` et plusieurs constantes de ce type.

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

- `dmy` Spécifie le jour, le mois et l’année de la commande, comme dans 2 décembre 1979.

- `mdy` Spécifie l’ordre mois, jour, année, comme le 2 décembre 1979.

- `ymd` Spécifie l’année, le mois, le jour de la commande, comme dans 1979/12/2.

- `ydm` Spécifie l’année, le jour et le mois de la commande, comme dans 1979:2 Dec.

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
