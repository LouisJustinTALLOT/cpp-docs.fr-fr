---
title: Sockaddr_in, Structure | Documents Microsoft
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
ms.openlocfilehash: aeb9e61f94ddd5f41ff3de26728c1fbe155f809d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373636"
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
 Famille d’adresses (doit être **AF_INET**).  
  
 *sin_port*  
 Port IP.  
  
 *sin_addr*  
 Adresse IP.  
  
 *Sin_zero*  
 Remplissage afin que structure de la même taille que `SOCKADDR`.  
  
## <a name="remarks"></a>Notes  
 C’est la forme de la `SOCKADDR` structure spécifique pour la famille d’adresses Internet et peut être converti en `SOCKADDR`.  
  
 Le composant d’adresse IP de cette structure est de type **IN_ADDR**. Le **IN_ADDR** structure est définie dans le fichier d’en-tête Windows Sockets WINSOCK. H comme suit :  
  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winsock2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR, structure](../../mfc/reference/sockaddr-structure.md)
