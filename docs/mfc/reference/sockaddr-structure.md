---
title: Structure SOCKADDR | Documents Microsoft
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
ms.openlocfilehash: f468a0a68dcfedab3b92deea492b48f7876c1610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371606"
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
 *sa_family*  
 Famille d’adresses de socket.  
  
 *sa_data*  
 Taille maximale de toutes les structures d’adresse de socket différentes.  
  
## <a name="remarks"></a>Notes  
 Kit de développement de Sockets de TCP/IP Microsoft prend uniquement en charge les domaines d’adresse Internet. Pour remplir les valeurs pour chaque partie d’une adresse en fait, vous utilisez la `SOCKADDR_IN` structure de données, qui est spécifiquement pour ce format d’adresse. Le `SOCKADDR` et `SOCKADDR_IN` des structures de données ont la même taille. Vous effectuez un cast simplement pour basculer entre les types de structure.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winsock2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Sockaddr_in, Structure](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

