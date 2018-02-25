---
title: CHAIN_PROPERTY_SET | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 634ab21ef9ffa18e5c18efa9078eb0606f9ff387
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
Cette macro chaîne ensemble les groupes de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ChainClass*  
 [in] Le nom de la classe pour les propriétés de la chaîne pour. Il s’agit d’une classe générée par l’Assistant Projet ATL qui contient déjà un mappage (par exemple, une session, les commandes ou les données source classe d’objet).  
  
## <a name="remarks"></a>Notes  
 Vous pouvez chaîner un jeu de propriétés à votre propre classe à partir d’une autre classe, puis accéder aux propriétés directement à partir de votre classe.  
  
> [!CAUTION]
>  Utilisez cette macro avec parcimonie. Utilisation incorrecte peut entraîner un consommateur à échouer les tests de compatibilité OLE DB.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)