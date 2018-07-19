---
title: Classe de collection Helpers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6607f70a18734310d184c5cdd05d1e87f1b82d35
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852345"
---
# <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection
Les classes de collection `CMap`, `CList`, et `CArray` utiliser des fonctions d’assistance globales basé sur un modèle fins telles que la comparaison, la copie et la sérialisation des éléments. Dans le cadre de votre implémentation de classes basées sur `CMap`, `CList`, et `CArray`, vous devez substituer ces fonctions en fonction des besoins avec des versions adaptées au type de données stockées dans votre carte, une liste ou un tableau. Pour plus d’informations sur les fonctions d’assistance de substitution comme `SerializeElements`, consultez l’article [Collections : comment définir une Collection de Type sécurisé](../../mfc/how-to-make-a-type-safe-collection.md). Notez que `ConstructElements` et `DestructElements` ont été déconseillées.  
  
 La bibliothèque Microsoft Foundation Class fournit les fonctions globales suivantes dans afxtempl.h pour vous aider à personnaliser vos classes de collection :  
  
### <a name="collection-class-helpers"></a>Programmes d’assistance pour les classes de collection  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|Indique si les éléments sont les mêmes.|  
|[CopyElements](#copyelements)|Copie les éléments d’un tableau à un autre.|  
|[DumpElements](#dumpelements)|Fournit une sortie de diagnostique orienté flux.|  
|[HashKey](#hashkey)|Calcule une clé de hachage.|  
|[SerializeElements](#serializeelements)|Stocke ou extrait des éléments vers ou à partir d’une archive.|  
  
##  <a name="compareelements"></a>  CompareElements  
 Appelé directement par [CList::Find] (clist-class.md #not_found.md #clist__find et indirectement par [cmap__lookup](cmap-class.md#lookup) et [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Le type du premier élément à comparer.  
  
 *pElement1*  
 Pointeur vers le premier élément à comparer.  
  
 *ARG_TYPE*  
 Le type du deuxième élément à comparer.  
  
 *pElement2*  
 Pointeur vers le deuxième élément à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet vers lequel pointe *pElement1* est égal à l’objet vers lequel pointé *pElement2*; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le `CMap` appelle utiliser le `CMap` paramètres de modèle *clé* et *ARG_KEY*.  
  
 L’implémentation par défaut retourne le résultat de la comparaison de  *\*pElement1* et  *\*pElement2*. Remplacez cette fonction pour qu’elle compare les éléments d’une manière qui convient à votre application.  
  
 Le langage C++ définit l’opérateur de comparaison ( `==`) pour les types simples (**char**, **int**, **float**, et ainsi de suite) mais ne définit ne pas un opérateur de comparaison pour les classes et structures. Si vous souhaitez utiliser `CompareElements` ou pour instancier une des classes de collection qui l’utilise, vous devez définir l’opérateur de comparaison ou de surcharge `CompareElements` avec une version qui renvoie les valeurs appropriées.  
  
### <a name="requirements"></a>Configuration requise  
   **En-tête :** afxtempl.h   
  
##  <a name="copyelements"></a>  CopyElements  
 Cette fonction est appelée directement par [CArray::Append](carray-class.md#append) et [CArray::Copy](carray-class.md#copy).  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type d’éléments à copier.  
  
 *pDest*  
 Pointeur vers la destination où les éléments sont copiés.  
  
 *pSrc*  
 Pointeur vers la source des éléments à copier.  
  
 *nCount*  
 Nombre d’éléments à copier.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut utilise l’opérateur d’assignation simple ( **=** ) pour effectuer l’opération de copie. Si le type en cours de copie n’a pas un opérateur surchargé =, l’implémentation par défaut effectue une copie au niveau du bit.  
  
 Pour plus d’informations sur l’implémentation de cela et autres fonctions d’assistance, consultez l’article [Collections : comment définir une Collection de Type sécurisé](../how-to-make-a-type-safe-collection.md).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxtempl.h  
  
##  <a name="dumpelements"></a>  DumpElements  
 Fournit une sortie de diagnostic orienté flux sous forme de texte pour les éléments de votre collection en cas de substitution.  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Paramètres  
 *dc*  
 Contexte pour vider des éléments de vidage.  
  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments.  
  
 *pElements*  
 Pointeur vers les éléments à être vidées.  
  
 *nCount*  
 Nombre d’éléments à être vidées.  
  
### <a name="remarks"></a>Notes  
 Le `CArray::Dump`, `CList::Dump`, et `CMap::Dump` fonctions appelez cette méthode si la profondeur de l’image mémoire est supérieure à 0.  
  
 L'implémentation par défaut n'exécute aucune opération. Si les éléments de votre collection sont dérivés de `CObject`, votre remplacement sera généralement itérer au sein des éléments de la collection, appelant `Dump` pour chaque élément à son tour.  
  

### <a name="requirements"></a>Configuration requise  
  **En-tête** afxtempl.h  
  
##  <a name="hashkey"></a>  HashKey  
 Calcule une valeur de hachage pour la clé donnée.  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>Paramètres  
 *ARG_KEY*  
 Paramètre de modèle qui spécifie le type de données permettant d’accéder aux clés de carte.  
  
 *key*  
 Clé dont la valeur hachage doit être calculé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de hachage de la clé.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée directement par [CMap::RemoveKey](cmap-class.md#removekey) et indirectement par [CMap::Lookup](cmap-class.md#lookup) et [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).
  
 L’implémentation par défaut crée une valeur de hachage en décalant *clé* droite par quatre positions. Remplacez cette fonction afin qu’elle retourne des valeurs de hachage appropriée pour votre application.  
  
### <a name="example"></a>Exemple
 ```cpp  
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number 
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
 ```
 
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxtempl.h 
  
##  <a name="serializeelements"></a>  SerializeElements  
 [CArray](carray-class.md), [CList](clist-class.md), et [CMap](cmap-class.md) appelez cette fonction pour sérialiser des éléments.  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments.  
  
 *ar*  
 Objet archive à archiver à partir d’ou.  
  
 *pElements*  
 Pointeur vers les éléments à archiver.  
  
 *nCount*  
 Nombre d’éléments archivés  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut est une opération de bits lire ou écrire.  
  
 Pour plus d’informations sur l’implémentation de cela et autres fonctions d’assistance, consultez l’article [Collections : comment définir une Collection de Type sécurisé](../how-to-make-a-type-safe-collection.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans l’article [Collections : comment définir une Collection de Type sécurisé](../how-to-make-a-type-safe-collection.md).  
 
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxtempl.h 
    
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [CMap (classe)](cmap-class.md)   
 [CList (classe)](clist-class.md)   
 [CArray, classe](carray-class.md)