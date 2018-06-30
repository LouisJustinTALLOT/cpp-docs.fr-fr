---
title: CTypedPtrArray (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9082e28aad1edc584a1796d5bb5e97b5601753f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122913"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray (classe)
Fournit un « wrapper » de type sécurisé pour les objets de la classe `CPtrArray` ou `CObArray`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Paramètres  
 *BASE_CLASS*  
 Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( `CObArray` ou `CPtrArray`).  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|Ajoute un nouvel élément à la fin d’un tableau. Le tableau est étendu si nécessaire|  
|[CTypedPtrArray::Append](#append)|Ajoute le contenu d’un tableau à la fin d’un autre. Le tableau est étendu si nécessaire|  
|[CTypedPtrArray::Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|  
|[CTypedPtrArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|  
|[CTypedPtrArray::GetAt](#getat)|Retourne la valeur à un index donné.|  
|[CTypedPtrArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|  
|[CTypedPtrArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[[] De CTypedPtrArray::operator](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez `CTypedPtrArray` plutôt que `CPtrArray` ou `CObArray`, la fonctionnalité de vérification de type C++ vous aide à éliminer les erreurs provoquées par les types pointeur ne correspondent pas.  
  
 En outre, le `CTypedPtrArray` wrapper effectue une grande partie des opérations de cast qui serait nécessaire si vous avez utilisé `CObArray` ou `CPtrArray`.  
  
 Étant donné que tous les `CTypedPtrArray` fonctions sont en ligne, l’utilisation de ce modèle n’affecte pas considérablement la taille ou la vitesse de votre code.  
  
 Pour plus d’informations sur l’utilisation de `CTypedPtrArray`, consultez les articles [Collections](../../mfc/collections.md) et [Classes basées sur le modèle](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxtempl.h  
  
##  <a name="add"></a>  CTypedPtrArray::Add  
 Cette fonction membre appelle `BASE_CLASS` **:: ajouter**.  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle spécifiant le type d’élément à ajouter au tableau.  
  
 *newElement*  
 L’élément à ajouter à ce tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de l’élément ajouté.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::Add](../../mfc/reference/cobarray-class.md#add).  
  
##  <a name="append"></a>  CTypedPtrArray::Append  
 Cette fonction membre appelle `BASE_CLASS`:: Append **.  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Paramètres  
 *BASE_CLASS*  
 Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
 *src*  
 Source des éléments à ajouter au tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du premier élément ajouté.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::Append](../../mfc/reference/cobarray-class.md#append).  
  
##  <a name="copy"></a>  CTypedPtrArray::Copy  
 Cette fonction membre appelle `BASE_CLASS` **:: copie**.  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Paramètres  
 *BASE_CLASS*  
 Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
 *src*  
 Source des éléments à copier dans un tableau.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).  
  
##  <a name="elementat"></a>  CTypedPtrArray::ElementAt  
 Cette fonction inline s’appelle `BASE_CLASS` **:: ElementAt**.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans ce tableau.  
  
 *nIndex*  
 Un index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence temporaire à l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre de modèle *TYPE*.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).  
  
##  <a name="getat"></a>  CTypedPtrArray::GetAt  
 Cette fonction inline s’appelle `BASE_CLASS` **:: GetAt**.  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.  
  
 *nIndex*  
 Un index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de l’élément à l’emplacement spécifié par *nIndex*. Cet élément est du type spécifié par le paramètre de modèle *TYPE*.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>  CTypedPtrArray::InsertAt  
 Cette fonction membre appelle `BASE_CLASS` **:: InsertAt**.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index entier qui peut être supérieur à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
 *newElement*  
 Le pointeur d’objet doit être placé dans ce tableau. A *newElement* de valeur **NULL** est autorisée.  
  
 *nCount*  
 Le nombre de fois que cet élément doit être inséré (par défaut 1).  
  
 *nStartIndex*  
 Un index entier qui peut être supérieur à la valeur retournée par `CObArray::GetUpperBound`.  
  
 *BASE_CLASS*  
 Classe de base de la classe de tableau de pointeurs typés. doit être une classe array ( [CObArray](../../mfc/reference/cobarray-class.md) ou [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *pNewArray*  
 Un autre tableau qui contient les éléments à ajouter à ce tableau.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).  
  
##  <a name="operator_at"></a>  [] De CTypedPtrArray::operator  
 Ces opérateurs inline appellent `BASE_CLASS` **:: opérateur []**.  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans le tableau.  
  
 *nIndex*  
 Un index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="remarks"></a>Notes  
 Le premier opérateur, est appelée pour les tableaux qui ne sont pas **const**, peut être utilisé sur la droite (r-value) ou sur la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour **const** tableaux, peut être utilisé uniquement sur la droite.  
  
 La version Debug de la bibliothèque déclare si l’indice (soit sur le côté gauche ou droit d’une instruction d’assignation) est hors limites.  
  
##  <a name="setat"></a>  CTypedPtrArray::SetAt  
 Cette fonction membre appelle `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
 *ptr*  
 Pointeur vers l’élément à insérer dans le tableau à la nIndex. Une valeur NULL est autorisée.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).  
  
##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow  
 Cette fonction membre appelle `BASE_CLASS` **:: SetAtGrow**.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index entier qui est supérieur ou égal à 0.  
  
 *TYPE*  
 Type des éléments stockés dans le tableau de classe de base.  
  
 *newElement*  
 Le pointeur d’objet à ajouter à ce tableau. A **NULL** la valeur est autorisée.  
  
### <a name="remarks"></a>Notes  
 Pour plus de la section Notes, consultez [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC COLLECT](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CPtrArray](../../mfc/reference/cptrarray-class.md)   
 [CObArray, classe](../../mfc/reference/cobarray-class.md)
