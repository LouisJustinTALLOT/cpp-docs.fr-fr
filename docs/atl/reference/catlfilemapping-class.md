---
title: Classe de CAtlFileMapping | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524e5d9c7cef5bcff0d72ddf1225ef79b1b26d64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358835"
---
# <a name="catlfilemapping-class"></a>Classe de CAtlFileMapping
Cette classe représente un fichier mappé en mémoire, l’ajout d’un opérateur de conversion pour les méthodes de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données utilisés pour l’opérateur de cast.  
  
## <a name="members"></a>Membres  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|Permet la conversion implicite de `CAtlFileMapping` objets `T` **\***.|  
  
## <a name="remarks"></a>Notes  
 Cette classe ajoute un opérateur de conversion unique pour permettre une conversion implicite de `CAtlFileMapping` objets `T` **\***. D’autres membres sont fournis par la classe de base [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlfile.h  
  
##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *  
 Permet la conversion implicite de `CAtlFileMapping` objets `T` **\***.  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `T` **\*** pointeur au début du fichier mappé en mémoire.  
  
### <a name="remarks"></a>Notes  
 Appels [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) et réinterprète le pointeur retourné comme un `T` **\*** où *T* est le type utilisé comme modèle paramètre de cette classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
