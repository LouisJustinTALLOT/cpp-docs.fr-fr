---
title: BEGIN_PROPSET_MAP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b1596797672c0fff92531ff90f67b94bfd6101e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089462"
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
Marque le début de la propriété définie les entrées de mappage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Classe*  
 [in] La classe dans laquelle cette propriété la valeur est spécifiée. Un jeu de propriétés peut être spécifié dans les objets OLE DB suivants :  
  
-   [Objets Source de données](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [Objets de session](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [Commandes](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>Exemple  
 Voici un exemple de mappage de jeu de propriétés :  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)