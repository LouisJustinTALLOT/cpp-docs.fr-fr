---
title: Classe de Platform::Collections::BackInsertIterator | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0be32b550cd0e19facb127ca6a052b03ef1eaf5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090016"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator, classe
Représente un itérateur qui ne remplace pas les éléments mais les insère dans le back end d'une collection séquentielle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type d'élément de la collection active.  
  
### <a name="remarks"></a>Notes  
 La classe BackInsertIterator implémente les règles requises par la [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md).  
  
### <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[BackInsertIterator::BackInsertIterator](#ctor)|Initialise une nouvelle instance de la classe BackInsertIterator.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[BackInsertIterator::operator*, opérateur](#operator-dereference)|Extrait une référence au BackInsertIterator actif.|  
|[BackInsertIterator::operator++, opérateur](#operator-increment)|Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.|  
|[BackInsertIterator::operator=, opérateur](#operator-assign)|Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `BackInsertIterator`  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** collection.h  
  
 **Espace de noms :** Platform::Collections  
  
---
## <a name="ctor"></a>  BackInsertIterator::BackInsertIterator (constructeur)
Initialise une nouvelle instance de la classe `BackInsertIterator`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `v`  
 Un IVector\<T > objet.  
  
### <a name="remarks"></a>Notes  
 Un `BackInsertIterator` insère des éléments après le dernier élément de l'objet spécifié par le paramètre `v`.  
 
## <a name="operator-assign"></a>  BackInsertIterator::operator = (opérateur)
Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `t`  
 Objet à ajouter à la collection actuelle.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence au BackInsertIterator actif.  

## <a name="operator-dereference"></a>  Opérateur de BackInsertIterator::operator
Extrait une référence au BackInsertIterator actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence au BackInsertIterator actif.  
  
### <a name="remarks"></a>Notes  
 Cet opérateur retourne une référence au BackInsertIterator actif, et non à un élément dans la collection actuelle.  
 
## <a name="operator-increment"></a>  BackInsertIterator::operator ++ (opérateur)
Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence au BackInsertIterator actif.  
  
### <a name="remarks"></a>Notes  
 Par conception, le premier exemple de syntaxe préincrémente le BackInsertIterator actuel et la deuxième syntaxe postincrémente le BackInsertIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.  
  
 Toutefois, cet opérateur ne modifie pas réellement le BackInsertIterator. Au lieu de cela, l'opérateur retourne une référence à l'itérateur actuel non modifié. Il s’agit du même comportement que [opérateur *](#dereference-operator).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)