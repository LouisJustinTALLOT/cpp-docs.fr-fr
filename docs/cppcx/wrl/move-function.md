---
title: Move (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 8d7c959ecb2d3c06872871ba062d2be603489141
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398171"
---
# <a name="move-function"></a>Move (fonction)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de l’argument.

*arg*<br/>
Un argument à déplacer.

## <a name="return-value"></a>Valeur de retour

Paramètre *arg* après les caractéristiques de référence ou référence rvalue, le cas échéant, ont été supprimés.

## <a name="remarks"></a>Notes

Déplace l’argument spécifié à partir d’un emplacement vers un autre.

Pour plus d’informations, consultez le **sémantique déplacer** section de [déclarateur de référence Rvalue : & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)