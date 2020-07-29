---
title: operator!=, opérateur (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator!=
ms.assetid: 785435da-87a6-4454-9bce-9d288a96dc26
ms.openlocfilehash: af7088348cd3f52b38f0277fb7d0a973a1ca0e4b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226891"
---
# <a name="operator-operator-microsoftwrl"></a>operator!=, opérateur (Microsoft::WRL)

Opérateur d’inégalité pour les objets [ComPtr](comptr-class.md) et [ComPtrRef](comptrref-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Paramètres

*un*<br/>
Objet gauche.

*p*<br/>
Objet droit.

## <a name="return-value"></a>Valeur de retour

**`true`** Si les objets ne sont pas égaux ; Sinon, **`false`** .

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
