---
title: Classe CManualAccessor | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b8efc46971b1aa72f8c5e572aa540bfed250d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098171"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor, classe
Représente un type d’accesseur conçu pour une utilisation avancée.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|Ajoute une entrée de liaison pour les colonnes de sortie.|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|Ajoute une entrée de paramètre dans l’accesseur de paramètre.|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|Alloue de la mémoire pour la colonne des structures de liaison et initialise les membres de données de colonne.|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|Alloue de la mémoire pour le paramètre de structures de liaison et initialise les membres de données de paramètre.|  
  
## <a name="remarks"></a>Notes  
 À l’aide de `CManualAccessor`, vous pouvez spécifier le paramètre et liaison de colonne de sortie par les appels de fonction de l’exécution.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [DBViewer](../../visual-cpp-samples.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (classe)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor (classe)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor, classe](../../data/oledb/cdynamicparameteraccessor-class.md)