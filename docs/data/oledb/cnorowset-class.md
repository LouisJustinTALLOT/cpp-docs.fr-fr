---
title: Cnorowset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e92c9bfb49bbb64faca633f04bb87f40028b6e1e
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339560"
---
# <a name="cnorowset-class"></a>CNoRowset, classe
Peut être utilisé comme argument template (`TRowset`) pour [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
### <a name="parameters"></a>Paramètres  
 *TAccessor*  
 Classe d’accesseur. La valeur par défaut est `CAccessorBase`.  
  
## <a name="remarks"></a>Notes  
 Utilisez `CNoRowset` comme argument de modèle si la commande ne renvoie pas un ensemble de lignes.  
  
 `CNoRowset` implémente les méthodes stub suivantes, chacune d’elles correspondent à d’autres méthodes de classe d’accesseur :  
  
-   `BindFinished` : Indique quand la liaison est terminée (retourne `S_OK`).  
  
-   `Close` -Libère des lignes et l’interface IRowset actuelle.  
  
-   `GetIID` -Récupère l’ID d’interface d’un point de connexion.  
  
-   `GetInterface` -Récupère une interface.  
  
-   `GetInterfacePtr` -Récupère un pointeur d’interface encapsulé.  
  
-   `SetAccessor` -Définit un pointeur vers l’accesseur.  
  
-   `SetupOptionalRowsetInterfaces` -Définit les interfaces facultatives pour l’ensemble de lignes.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)