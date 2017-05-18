---
title: Classe de CHeapPtrBase | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8084104489f6f1e2358ce0cbb573f4e20a0c4fce
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptrbase-class"></a>CHeapPtrBase (classe)
Cette classe constitue la base pour plusieurs classes de pointeur intelligent de segment de mémoire.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type d’objet à stocker sur le tas.  
  
 `Allocator`  
 La classe de l’allocation de mémoire à utiliser. Par défaut les routines de la bibliothèque CRT sont utilisés pour allouer et libérer de la mémoire.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrBase :: ~ CHeapPtrBase](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Appelez cette méthode pour allouer de la mémoire.|  
|[CHeapPtrBase::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|  
|[CHeapPtrBase::Detach](#detach)|Appelez cette méthode pour libérer la possession d’un pointeur.|  
|[CHeapPtrBase::Free](#free)|Appelez cette méthode pour supprimer un objet vers lequel pointé un `CHeapPtrBase`.|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Appelez cette méthode pour réallouer de la mémoire.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|L’opérateur de cast.|  
|[CHeapPtrBase::operator se](#operator_amp)|Le s’opérateur.|  
|[CHeapPtrBase::operator->](#operator_ptr)|Opérateur pointeur vers membre.|  

  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|La variable de membre de données de pointeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe constitue la base pour plusieurs classes de pointeur intelligent de segment de mémoire. Les classes dérivées, par exemple, [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), ajouter leurs propres constructeurs et des opérateurs. Consultez ces classes pour les exemples d’implémentation.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcore.h  
  
##  <a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes  
 Appelez cette méthode pour allouer de la mémoire.  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Le nombre d’octets de mémoire à allouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si la mémoire est correctement alloué, false dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Dans les versions debug, un échec d’assertion se produit si le [CHeapPtrBase::m_pData](#m_pdata) variable membre pointe actuellement à une valeur ; autrement dit, il n’est pas égal à NULL.  
  
##  <a name="attach"></a>CHeapPtrBase::Attach  
 Appelez cette méthode pour prendre possession d’un pointeur existant.  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pData`  
 Le `CHeapPtrBase` objet prendra possession de ce pointeur.  
  
### <a name="remarks"></a>Remarques  
 Lorsqu’un `CHeapPtrBase` objet prend possession du pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il devient hors de portée.  
  
 Dans les versions debug, un échec d’assertion se produit si le [CHeapPtrBase::m_pData](#m_pdata) variable membre pointe actuellement à une valeur ; autrement dit, il n’est pas égal à NULL.  
  
##  <a name="dtor"></a>CHeapPtrBase :: ~ CHeapPtrBase  
 Destructeur.  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>Remarques  
 Libère toutes les ressources attribuées.  
  
##  <a name="detach"></a>CHeapPtrBase::Detach  
 Appelez cette méthode pour libérer la possession d’un pointeur.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une copie du pointeur.  
  
### <a name="remarks"></a>Remarques  
 Libère la possession d’un pointeur, définit les [CHeapPtrBase::m_pData](#m_pdata) variable de membre avec la valeur NULL et retourne une copie du pointeur.  
  
##  <a name="free"></a>CHeapPtrBase::Free  
 Appelez cette méthode pour supprimer un objet vers lequel pointé un `CHeapPtrBase`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’objet pointé par le `CHeapPtrBase` est libéré et la [CHeapPtrBase::m_pData](#m_pdata) variable membre a la valeur NULL.  
  
##  <a name="m_pdata"></a>CHeapPtrBase::m_pData  
 La variable de membre de données de pointeur.  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>Remarques  
 Cette variable membre conserve les informations de pointeur.  
  
##  <a name="operator_amp"></a>CHeapPtrBase::operator&amp;  
 Le s’opérateur.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’adresse de l’objet vers lequel pointé le `CHeapPtrBase` objet.  
  

##  <a name="operator_ptr"></a>CHeapPtrBase::operator-&gt;  

 Opérateur pointeur vers membre.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la [CHeapPtrBase::m_pData](#m_pdata) variable membre.  
  
### <a name="remarks"></a>Notes  
 Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointée le `CHeapPtrBase` objet. Dans les versions debug, un échec d’assertion se produit si le `CHeapPtrBase` pointe sur la valeur NULL.  
  
##  <a name="operator_t_star"></a>CHeapPtrBase::operator T *  
 L’opérateur de cast.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Remarques  
 Retourne [CHeapPtrBase::m_pData](#m_pdata).  
  
##  <a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes  
 Appelez cette méthode pour réallouer de la mémoire.  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Le volume de mémoire à allouer, en octets.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si la mémoire est correctement alloué, false dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [CHeapPtr (classe)](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr (classe)](../../atl/reference/ccomheapptr-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

