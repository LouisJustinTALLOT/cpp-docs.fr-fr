---
title: Sockaddr_in, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e5ec6ebf4329ff03c75240dc7cec93e9ba46331
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885736"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN, structure
Dans la famille d’adresses Internet, le `SOCKADDR_IN` structure est utilisée par Windows Sockets pour spécifier une adresse de point de terminaison local ou distant auquel se connecter un socket.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct sockaddr_in{  
    short sin_family;  
    unsigned short sin_port;  
struct in_addr sin_addr;  
    char sin_zero[8];  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sin_family*  
 Famille d’adresses (doit être le AF_INET).  
  
 *sin_port*  
 Port IP.  
  
 *sin_addr*  
 Adresse IP.  
  
 *Sin_zero*  
 Remplissage à donner à la même taille que la structure `SOCKADDR`.  
  
## <a name="remarks"></a>Notes  
 C’est la forme de la `SOCKADDR` structure spécifique à la famille d’adresses Internet et pouvant être casté en `SOCKADDR`.  
  
 Le composant d’adresse IP de cette structure est de type `IN_ADDR`. Le `IN_ADDR` structure est définie dans le fichier d’en-tête Windows Sockets WINSOCK. H comme suit :  
  
```  
struct in_addr {
    union {
        struct {  
            unsigned char s_b1, s_b2, s_b3, s_b4;  
        } S_un_b;  
        struct {  
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winsock2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR, structure](../../mfc/reference/sockaddr-structure.md)
