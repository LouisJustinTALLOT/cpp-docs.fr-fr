---
title: time_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685786"
---
# <a name="time_base-class"></a>time_base, classe

La classe sert de classe de base pour les facettes du modèle de classe time_get, en définissant uniquement le type énuméré `dateorder` et plusieurs constantes de ce type.

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

- `no_order` spécifie aucun ordre particulier.

- `dmy` spécifie le jour, le mois et l’année de la commande, comme dans 2 décembre 1979.

- `mdy` spécifie l’ordre mois, jour, année, comme le 2 décembre 1979.

- `ymd` spécifie l’année, le mois, le jour de la commande, comme dans 1979/12/2.

- `ydm` spécifie l’année, le jour et le mois de la commande, comme dans 1979:2 Dec.

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
