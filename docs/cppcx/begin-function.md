---
description: 'En savoir plus sur : fonction Begin'
title: begin (fonction)
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: ae59a4b4344da520d86c216f4c9979953e16753c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302762"
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
Collection d’objets Vector \<T> ou vectorview \<T> accessibles par une \<T> interface IVector ou IVectorView \<T> .

*i*<br/>
Collection d’objets Windows Runtime arbitraires accessibles par une \<T> interface interface iiterable.

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui pointe vers le début de la collection.

### <a name="remarks"></a>Notes

Les deux premières fonctions de modèle retournent des itérateurs et la troisième fonction de modèle retourne un itérateur d'entrée.

L’objet VectorIterator retourné par Begin est un itérateur de proxy qui stocke des éléments de type VectorProxy \<T> . Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Windows::Foundation::Collections

## <a name="see-also"></a>Voir aussi

[Windows :: Foundation :: Collections, espace de noms](../cppcx/windows-foundation-collections-namespace-c-cx.md)
