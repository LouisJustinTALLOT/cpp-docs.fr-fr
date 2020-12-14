---
description: 'En savoir plus sur : fonction back_inserter'
title: back_inserter (fonction)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: d2483c9947fbf3a7bc04024221ec6e582e416f84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223579"
---
# <a name="back_inserter-function"></a>back_inserter (fonction)

Retourne un itérateur qui est utilisé pour insérer des éléments à la fin de la collection spécifiée.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de type de modèle.

*v*<br/>
Pointeur d'interface qui permet d'accéder à la collection sous-jacente.

### <a name="return-value"></a>Valeur renvoyée

Itérateur.

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows :: Foundation :: Collections, espace de noms](../cppcx/windows-foundation-collections-namespace-c-cx.md)
