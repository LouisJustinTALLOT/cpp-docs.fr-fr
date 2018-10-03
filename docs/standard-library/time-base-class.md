---
title: time_base, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e4e371bd242dff337450fd87527455b50556afc
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235774"
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
