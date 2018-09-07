---
title: End Function | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::end
dev_langs:
- C++
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff953d33fb882bf65af101c422093ddbc1aedf2e
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105231"
---
# <a name="end-function"></a>end (fonction)

Retourne un itérateur qui pointe au-delà de la fin d'une collection accessible par le paramètre d'interface spécifié.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de type de modèle.

*v*<br/>
Une collection de vecteur\<T > ou VectorView\<T > les objets qui sont accessibles par un IVector\<T >, ou IVectorView\<T > interface.

*i*<br/>
Collection d’arbitraires Windows Runtime objets qui sont accessibles par un IIterable\<T > interface.

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe au-delà de la fin de la collection.

### <a name="remarks"></a>Notes

Les deux premières fonctions de modèle retournent des itérateurs et la troisième fonction de modèle retourne un itérateur d'entrée.

L'objet [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) retourné par `end` est un itérateur de proxy qui stocke des éléments de type `VectorProxy<T>`. Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows::Foundation :: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)