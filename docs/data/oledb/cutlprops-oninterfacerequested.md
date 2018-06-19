---
title: CUtlProps::OnInterfaceRequested | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50a1f17294a91446e71a51ffdac6c5aec83f2c9a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099769"
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
Gère les demandes d’une interface facultative lorsqu’un consommateur appelle une méthode sur l’un de l’objet des interfaces de création.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 [in] L’IID de l’interface demandée. Pour plus d’informations, consultez la description de la `riid` paramètre de `ICommand::Execute` dans les *de référence du programmeur OLE DB* (dans le *MDAC SDK*).  
  
## <a name="remarks"></a>Notes  
 **OnInterfaceRequested** gère les demandes de consommateur d’une interface facultative lorsqu’un consommateur appelle une méthode sur l’un de l’objet des interfaces de création (tel que **IDBCreateSession**, **IDBCreateCommand**, `IOpenRowset`, ou `ICommand`). Il définit la propriété OLE DB correspondante pour l’interface demandée. Par exemple, si le consommateur demande **IID_IRowsetLocate**, **OnInterfaceRequested** définit le **DBPROP_IRowsetLocate** interface. Cela tient à jour l’état approprié lors de la création de l’ensemble de lignes.  
  
 Cette méthode est appelée lorsque le consommateur appelle **IOpenRowset::OpenRowset** ou `ICommand::Execute`.  
  
 Si un consommateur ouvre un objet et demande une interface facultative, le fournisseur doit définir la propriété associée à cette interface pour `VARIANT_TRUE`. Pour permettre le traitement spécifique à la propriété, **OnInterfaceRequested** est appelée avant que le fournisseur **Execute** méthode est appelée. Par défaut, **OnInterfaceRequested** gère les interfaces suivantes :  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 Si vous souhaitez gérer d’autres interfaces, remplacez cette fonction dans votre classe de source, de session, de commande ou d’ensemble de lignes de données pour les fonctions de processus. Votre substitution doit passer par les interfaces de propriétés set/get normal pour vous assurer que définir des propriétés définit également des propriétés chaînées (consultez [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CUtlProps, classe](../../data/oledb/cutlprops-class.md)