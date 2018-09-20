---
title: Linger, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LINGER
dev_langs:
- C++
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dda3aab3c4a967c82a699058868edc8fc183984
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386377"
---
# <a name="linger-structure"></a>LINGER, structure

Le `LINGER` structure est utilisée pour manipuler les options SO_LINGER et SO_DONTLINGER de `CAsyncSocket::GetSockOpt`.

## <a name="syntax"></a>Syntaxe

```
struct linger {
    u_short l_onoff;            // option on/off
    u_short l_linger;           // linger time
};
```

## <a name="remarks"></a>Notes

Définition de l’option SO_DONTLINGER empêche le blocage sur la fonction membre `Close` en attendant des données non envoyées à envoyer. Définition de cette option revient à définir SO_LINGER avec `l_onoff` défini sur 0.

## <a name="requirements"></a>Configuration requise

**En-tête :** winsock2.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)<br/>
[CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

