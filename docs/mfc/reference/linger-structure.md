---
title: LINGER, structure
ms.date: 11/04/2016
f1_keywords:
- LINGER
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
ms.openlocfilehash: 78f1a5ce993373ea9e477262f0779515c52dbd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495315"
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

