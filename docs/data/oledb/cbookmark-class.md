---
title: CBookmark, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c14fde6fb07a35ef9e2955ce61f991bede6b11a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094749"
---
# <a name="cbookmark-class"></a>CBookmark, classe
Contient une valeur de signet dans sa mémoire tampon.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nSize`  
 La taille de la mémoire tampon du signet en octets. Lorsque `nSize` est égal à zéro, la mémoire tampon de signet sera créée dynamiquement au moment de l’exécution.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|Le constructeur|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|Récupère le pointeur vers la mémoire tampon.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|Récupère la taille de la mémoire tampon en octets.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Définit la valeur du signet.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur =](../../data/oledb/cbookmark-operator-equal.md)|Assigne un `CBookmark` classe vers un autre.|  
  
## <a name="remarks"></a>Notes  
 **CBookmark\<0 >** est une spécialisation de modèle de `CBookmark`; sa mémoire tampon est créé dynamiquement au moment de l’exécution.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)