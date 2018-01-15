---
title: Classe de IAtlStringMgr | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs: C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85b99b0b1f35ecbc35b4096ac8c2260d0a55680d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="iatlstringmgr-class"></a>Classe de IAtlStringMgr
Cette classe représente l’interface pour un `CStringT` Gestionnaire de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Allouer](#allocate)|Appelez cette méthode pour allouer une nouvelle structure de données de chaîne.|  
|[Clone](#clone)|Appelez cette méthode pour retourner un pointeur vers un nouveau gestionnaire de chaîne pour une utilisation avec une autre instance de `CSimpleStringT`.|  
|[Gratuit](#free)|Appelez cette méthode pour libérer une structure de données de chaîne.|  
|[GetNilString](#getnilstring)|Retourne un pointeur vers le `CStringData` objet utilisé par les objets de la chaîne vide.|  
|[Réallouer](#reallocate)|Appelez cette méthode pour réallouer une structure de données de chaîne.|  
  
## <a name="remarks"></a>Notes  
 Cette interface gère la mémoire utilisée par les classes de chaîne indépendant des MFC ; comme [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), et [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).  
  
 Vous pouvez également utiliser cette classe pour implémenter un gestionnaire de mémoire personnalisés pour votre classe de chaîne personnalisée. Pour plus d’informations, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlsimpstr.h  
  
##  <a name="allocate"></a>IAtlStringMgr::Allocate  
 Alloue une nouvelle structure de données de chaîne.  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nAllocLength`  
 Le nombre de caractères dans le nouveau bloc de mémoire.  
  
 `nCharSize`  
 La taille (en octets) du type de caractère utilisé par le Gestionnaire de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le bloc de mémoire nouvellement alloué.  
  
> [!NOTE]
>  Pas signaler un échec d’allocation en levant une exception. Au lieu de cela, un échec d’allocation doit être signalé en retournant **NULL**.  
  
### <a name="remarks"></a>Notes  
 Appelez [IAtlStringMgr::Free](#free) ou [IAtlStringMgr::ReAllocate](#reallocate) pour libérer la mémoire allouée par cette méthode.  
  
> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="clone"></a>IAtlStringMgr::Clone  
 Retourne un pointeur vers un nouveau gestionnaire de chaîne pour une utilisation avec une autre instance de `CSimpleStringT`.  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une copie de la `IAtlStringMgr` objet.  
  
### <a name="remarks"></a>Notes  
 Appelé par le framework lorsqu’un gestionnaire de chaînes est nécessaire pour une nouvelle chaîne. Dans la plupart des cas, le **cela** pointeur est retourné.  
  
 Toutefois, si le Gestionnaire de mémoire ne prend pas en charge utilisé par plusieurs instances de `CSimpleStringT`, un pointeur vers un gestionnaire de chaînes partageable doit être retourné.  
  
> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="free"></a>IAtlStringMgr::Free  
 Libère une structure de données de chaîne.  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pData`  
 Pointeur vers le bloc de mémoire à libérer.  
  
### <a name="remarks"></a>Notes  
 Libère le bloc de mémoire spécifié précédemment alloué par [Allocate](#allocate) ou [réallouer](../../atl/reference/iatlmemmgr-class.md#reallocate).  
  
> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 Retourne un pointeur vers une structure de données de chaîne pour une chaîne vide.  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CStringData` objet utilisé pour représenter une chaîne vide.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour retourner une représentation d’une chaîne vide.  
  
> [!NOTE]
>  Lorsque vous implémentez un gestionnaire personnalisé, cette fonction ne doit jamais échouer. Vous pouvez vous assurer par incorporation d’une instance de **CNilStringData** dans la classe de gestionnaire de chaîne et retournent un pointeur à cette instance.  
  
> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="reallocate"></a>IAtlStringMgr::Reallocate  
 Réalloue une structure de données de chaîne.  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pData`  
 Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.  
  
 `nAllocLength`  
 Le nombre de caractères dans le nouveau bloc de mémoire.  
  
 `nCharSize`  
 La taille (en octets) du type de caractère utilisé par le Gestionnaire de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour redimensionner le bloc de mémoire existant spécifié par `pData`.  
  
 Appelez [IAtlStringMgr::Free](#free) pour libérer la mémoire allouée par cette méthode.  
  
> [!NOTE]
>  Pour obtenir des exemples, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


