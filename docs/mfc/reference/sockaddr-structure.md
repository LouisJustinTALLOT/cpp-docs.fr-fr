---
title: SOCKADDR, structure
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
ms.openlocfilehash: 68d5261c6520b5baee8495b72a0b9d234a35a185
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543843"
---
# <a name="sockaddr-structure"></a>SOCKADDR, structure

Le `SOCKADDR` structure est utilisée pour stocker une adresse IP (Internet Protocol) pour un ordinateur participant à une communication de Windows Sockets.

## <a name="syntax"></a>Syntaxe

```
struct sockaddr {
    unsigned short sa_family;
    char sa_data[14];
};
```

#### <a name="parameters"></a>Paramètres

*sa_family*<br/>
Famille d’adresses de socket.

*sa_data*<br/>
Taille maximale de toutes les structures d’adresse de socket différentes.

## <a name="remarks"></a>Notes

Kit de développement de Sockets de TCP/IP Microsoft prend uniquement en charge les domaines d’adresse Internet. Pour remplir les valeurs pour chaque partie d’une adresse en fait, vous utilisez le `SOCKADDR_IN` structure de données, qui est spécifiquement pour ce format d’adresse. Le `SOCKADDR` et `SOCKADDR_IN` des structures de données ont la même taille. Vous simplement effectuer un cast pour basculer entre les types de deux structures.

## <a name="requirements"></a>Configuration requise

**En-tête :** winsock2.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR_IN, structure](../../mfc/reference/sockaddr-in-structure.md)<br/>
[CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)<br/>
[CSocket::Create](../../mfc/reference/csocket-class.md#create)

