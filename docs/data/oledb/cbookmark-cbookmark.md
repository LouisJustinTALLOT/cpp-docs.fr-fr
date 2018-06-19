---
title: CBookmark::CBookmark | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7663c34fc9eea5f4262fea6b347c1b7899ace85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095233"
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
Constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CBookmark();   

CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nSize`  
 [in] Taille de la mémoire tampon du signet en octets.  
  
## <a name="remarks"></a>Notes  
 La première fonction définit la mémoire tampon **NULL** et la taille de mémoire tampon à 0. La deuxième fonction définit la taille de mémoire tampon sur `nSize`et la mémoire tampon vers un tableau d’octets de `nSize` octets.  
  
> [!NOTE]
>  Cette fonction est disponible uniquement dans **CBookmark\<0 >**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CBookmark, classe](../../data/oledb/cbookmark-class.md)