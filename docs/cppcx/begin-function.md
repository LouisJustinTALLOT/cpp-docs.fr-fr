---
title: begin (fonction)
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741408"
---
# <a name="begin-function"></a>begin (fonction)

Retourne un itérateur qui pointe vers le début d'une collection accessible par le paramètre d'interface spécifié.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de type de modèle.

*v*<br/>
Une collection de vecteur\<T > ou VectorView\<T > les objets qui sont accessibles par un IVector\<T > ou IVectorView\<T > interface.

*i*<br/>
Une collection d’objets Windows Runtime arbitraires qui sont accessibles par un IIterable\<T > interface.

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe vers le début de la collection.

### <a name="remarks"></a>Notes

Les deux premières fonctions de modèle retournent des itérateurs et la troisième fonction de modèle retourne un itérateur d'entrée.

L’objet VectorIterator objet qui est retourné par begin est un itérateur de proxy qui stocke des éléments de type VectorProxy\<T >. Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows::Foundation :: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)
