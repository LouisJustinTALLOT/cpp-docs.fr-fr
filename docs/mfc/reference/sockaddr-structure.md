---
title: Sockaddr, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac6e433c0bbc70e6e1caa79599d5388aef49b4c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435283"
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

