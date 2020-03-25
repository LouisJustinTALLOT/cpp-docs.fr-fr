---
title: Move (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213705"
---
# <a name="move-function"></a>Move (fonction)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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
Argument à déplacer.

## <a name="return-value"></a>Valeur de retour

Le paramètre *arg* après la référence ou les traits de référence rvalue, le cas échéant, ont été supprimés.

## <a name="remarks"></a>Notes

Déplace l’argument spécifié d’un emplacement à un autre.

Pour plus d’informations, consultez la section relative à la **sémantique de déplacement** du [déclarateur de référence Rvalue : & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
