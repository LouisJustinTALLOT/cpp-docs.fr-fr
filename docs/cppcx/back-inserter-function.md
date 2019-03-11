---
title: back_inserter (fonction)
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750739"
---
# <a name="backinserter-function"></a>back_inserter (fonction)

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

### <a name="return-value"></a>Valeur de retour

Itérateur.

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows::Foundation :: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)
