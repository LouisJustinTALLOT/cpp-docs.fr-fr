---
title: CXMLAccessor::GetXMLRowData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 147a79a4d9db17ac0f418356ba45909d02d93c06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103149"
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
Récupère le contenu entier d’une table en tant que données de chaîne au format XML, par ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,   
   bool bAppend = false) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `strOutput`  
 [out] Une référence à une mémoire tampon contenant les données de table doit être récupéré. Les données sont formatées sous forme de données de chaîne avec des noms de balise XML qui correspondent aux noms de colonne du magasin de données.  
  
 *bAppend*  
 [in] Valeur booléenne spécifiant s’il faut ajouter une chaîne à la fin des données de sortie.  
  
## <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
## <a name="remarks"></a>Notes  
 L’exemple suivant montre comment les données de ligne sont au format XML. `DATA` ci-dessous représente les données de ligne. Utilisez les méthodes pour passer à la ligne souhaitée de déplacement.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CXMLAccessor, classe](../../data/oledb/cxmlaccessor-class.md)