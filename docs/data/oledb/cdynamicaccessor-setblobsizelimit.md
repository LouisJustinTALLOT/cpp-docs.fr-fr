---
title: CDynamicAccessor::SetBlobSizeLimit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8731857507fa096d500a31f31a7c31ef4f94cfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096078"
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
Définit la taille de l’objet BLOB en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nBlobSize`  
 Spécifie la limite de taille d’objet BLOB.  
  
## <a name="remarks"></a>Notes  
 Définit la taille de l’objet BLOB en octets ; données de la colonne est supérieurs à cette valeur sont traitées comme un objet BLOB. Certains fournisseurs offrent une très grande taille pour les colonnes (par exemple, 2 Go). Au lieu d’une tentative d’allocation de mémoire pour une colonne de cette taille, vous serez généralement essayer lier ces colonnes en tant qu’objets BLOB. De cette façon, vous ne devez allouer toute la mémoire, mais vous pouvez toujours lire toutes les données sans risque de troncation. Toutefois, il existe certains cas dans laquelle vous pouvez souhaiter forcer `CDynamicAccessor` pour lier des colonnes volumineuses dans leurs types de données natifs. Pour ce faire, appelez `SetBlobSizeLimit` avant d’appeler **ouvrir**.  
  
 La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit la taille maximale de BLOB à la valeur par défaut de 8 000 octets.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)