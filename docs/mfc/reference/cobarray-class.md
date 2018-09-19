---
title: CObArray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7598065aa451d87fb45ae26310064e4828b4fb72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098806"
---
# <a name="cobarray-class"></a>CObArray (classe)
Prend en charge des tableaux de pointeurs `CObject` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CObArray : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CObArray::CObArray](#cobarray)|Construit un tableau vide pour `CObject` des pointeurs.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CObArray::Add](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|  
|[CObArray::Append](#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|  
|[CObArray::Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|  
|[CObArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|  
|[CObArray::FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|  
|[CObArray::GetAt](#getat)|Retourne la valeur à un index donné.|  
|[CObArray::GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|  
|[CObArray::GetData](#getdata)|Autorise l'accès aux éléments du tableau. Peut être NULL.|  
|[CObArray::GetSize](#getsize)|Obtient le nombre d'éléments dans ce tableau.|  
|[CObArray::GetUpperBound](#getupperbound)|Retourne le plus grand index valide.|  
|[CObArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|  
|[CObArray::IsEmpty](#isempty)|Détermine si le tableau est vide.|  
|[CObArray::RemoveAll](#removeall)|Supprime tous les éléments de ce tableau.|  
|[CObArray::RemoveAt](#removeat)|Supprime un élément à un index spécifique.|  
|[CObArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|  
|[CObArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|  
|[CObArray::SetSize](#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[[] CObArray::operator](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|  
  
## <a name="remarks"></a>Notes  
 Ces tableaux d’objets est semblables aux tableaux C, mais ils peuvent dynamiquement réduire et évoluer si nécessaires.  
  
 Index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut corriger la limite supérieure ou autoriser le tableau développer lorsque vous ajoutez des éléments au-delà de la limite actuelle. Mémoire est allouée de façon contiguë à la limite supérieure, même si certains éléments sont null.  
  
 Sous Win32, la taille d’un `CObArray` objet est limité uniquement à la mémoire disponible.  
  
 Comme avec un tableau de C, le temps d’accès pour un `CObArray` élément indexé est constante et est indépendant de la taille du tableau.  
  
 `CObArray` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de `CObject` pointeurs est stocké dans une archive, avec l’opérateur d’insertion surchargé ou avec le `Serialize` fonction membre, chaque `CObject` élément est, à son tour, sérialisé, ainsi que son index de tableau.  
  
 Si vous avez besoin d’un dump de l’individu `CObject` éléments dans un tableau, vous devez définir la profondeur de la `CDumpContext` objet à 1 ou supérieur.  
  
 Quand un `CObArray` objet est supprimé, ou lorsque ses éléments sont supprimés, uniquement le `CObject` pointeurs sont supprimés, pas les objets qu’ils référencent.  
  
> [!NOTE]
>  Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.  
  
 Dérivation de classe de tableau est similaire à la dérivation de la liste. Pour plus d’informations sur la dérivation d’une classe à usage spécial liste, consultez l’article [Collections](../../mfc/collections.md).  
  
> [!NOTE]
>  Si vous prévoyez de sérialiser le tableau, vous devez utiliser la macro IMPLEMENT_SERIAL dans l’implémentation de votre classe dérivée.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcoll.h  
  
##  <a name="add"></a>  CObArray::Add  
 Ajoute un nouvel élément à la fin d’un tableau ne soit le tableau 1.  
  
```  
INT_PTR Add(CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *newElement*  
 Le `CObject` pointeur doit être ajouté à ce tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément ajouté.  
  
### <a name="remarks"></a>Notes  
 Si [SetSize](#setsize) a été utilisé avec un *nGrowBy* valeur supérieure à 1, puis de mémoire supplémentaire peut être allouée. Toutefois, la limite supérieure augmente de 1 uniquement.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::Add`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Ajouter INT_PTR (octets** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Ajouter INT_PTR (DWORD** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Ajouter INT_PTR (void** <strong>\*</strong> `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Ajouter INT_PTR (LPCTSTR** `newElement` **) ; lever (CMemoryException\* ) ;**<br /><br /> **INT_PTR Add(const CString&** `newElement` **) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Ajouter INT_PTR (UINT** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Ajouter INT_PTR (WORD** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```
  
##  <a name="append"></a>  CObArray::Append  
 Appelez cette fonction membre pour ajouter le contenu d’un autre tableau à la fin du tableau donné.  
  
```  
INT_PTR Append(const CObArray& src);
```  
  
### <a name="parameters"></a>Paramètres  
 *src*  
 Source des éléments à ajouter au tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du premier élément ajouté.  
  
### <a name="remarks"></a>Notes  
 Les tableaux doivent être du même type.  
  
 Si nécessaire, `Append` peut allouer de mémoire supplémentaire pour prendre en compte les éléments ajoutés au tableau.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::Append`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Ajouter INT_PTR (const CByteArray &** *src* **) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Ajout de INT_PTR (CDWordArray const &** *src* **) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Ajouter INT_PTR (const CPtrArray &** *src* **) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Ajout de INT_PTR (CStringArray const &** *src* **) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Ajout de INT_PTR (CUIntArray const &** *src* **) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Ajouter INT_PTR (const CWordArray &** *src* **) ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]  
  
##  <a name="copy"></a>  CObArray::Copy  
 Appelez cette fonction membre pour remplacer les éléments du tableau donné avec les éléments d’un autre tableau du même type.  
  
```  
void Copy(const CObArray& src);
```  
  
### <a name="parameters"></a>Paramètres  
 *src*  
 Source des éléments à copier dans le tableau.  
  
### <a name="remarks"></a>Notes  
 `Copy` ne pas libérer de la mémoire ; Toutefois, si nécessaire, `Copy` peut allouer de mémoire supplémentaire pour prendre en compte les éléments copiés dans le tableau.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::Copy`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void copie (const CByteArray &** *src* **) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void copie (CDWordArray const &** *src* **) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void copie (const CPtrArray &** *src* **) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void copie (CStringArray const &** *src* **) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void copie (CUIntArray const &** *src* **) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void copie (const CWordArray &** *src* **) ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]  
  
##  <a name="cobarray"></a>  CObArray::CObArray  
 Construit un vide `CObject` tableau de pointeurs.  
  
```  
CObArray();
```  
  
### <a name="remarks"></a>Notes  
 Le tableau développe un élément à la fois.  
  
 Le tableau suivant présente les autres constructeurs sont similaires aux `CObArray::CObArray`.  
  
|Classe|Constructeur|  
|-----------|-----------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**() CByteArray ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**() CDWordArray ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**() CPtrArray ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**() CStringArray ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**() CUIntArray ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**() CWordArray ;**|  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]  
  
##  <a name="elementat"></a>  CObArray::ElementAt  
 Retourne une référence temporaire au pointeur d'élément dans le tableau.  
  
```  
CObject*& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `GetUpperBound`.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à un `CObject` pointeur.  
  
### <a name="remarks"></a>Notes  
 Il est utilisé pour implémenter l’opérateur d’assignation de gauche pour les tableaux. Notez qu’il s’agit d’une fonction avancée qui doit être utilisée uniquement pour implémenter des opérateurs de tableau spéciaux.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::ElementAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**OCTETS & ElementAt (INT_PTR** `nIndex` **) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & ElementAt (INT_PTR** `nIndex` **) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**MOT & ElementAt (INT_PTR** `nIndex` **) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CObArray::GetSize](#getsize).  
  
##  <a name="freeextra"></a>  CObArray::FreeExtra  
 Libère la mémoire supplémentaire qui a été alloué tandis que le tableau a été augmenté.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::FreeExtra`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void () FreeExtra ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void () FreeExtra ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void () FreeExtra ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void () FreeExtra ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void () FreeExtra ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void () FreeExtra ;**|  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CObArray::GetData](#getdata).  
  
##  <a name="getat"></a>  CObArray::GetAt  
 Retourne l’élément de tableau à l’index spécifié.  
  
```  
CObject* GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `GetUpperBound`.  
  
### <a name="return-value"></a>Valeur de retour  
 Le `CObject` élément pointeur actuellement à cet index.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  En passant une valeur négative ou une valeur supérieure à la valeur retournée par `GetUpperBound` entraîne un échec d’assertion.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::GetAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**OCTETS GetAt (INT_PTR** `nIndex` **) const ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]  
  
##  <a name="getcount"></a>  CObArray::GetCount  
 Retourne le nombre d’éléments de tableau.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d’éléments dans le tableau.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les index sont de base zéro, la taille est 1 supérieur le plus grand index.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::GetCount`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR const ; (GetCount)**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR const ; (GetCount)**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR const ; (GetCount)**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR const ; (GetCount)**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR const ; (GetCount)**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR const ; (GetCount)**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]  
  
##  <a name="getdata"></a>  CObArray::GetData  
 Utilisez cette fonction membre pour obtenir un accès direct aux éléments dans le tableau.  
  
```  
const CObject** GetData() const;  
  
CObject** GetData();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le tableau de `CObject` des pointeurs.  
  
### <a name="remarks"></a>Notes  
 Si aucun élément n’est disponibles, `GetData` retourne une valeur null.  
  
 Bien que l’accès direct aux éléments d’un tableau peut vous aider à travailler plus rapidement, soyez prudent lors de l’appel `GetData`; les erreurs que vous apportez directement affectent les éléments de votre tableau.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::GetData`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**OCTETS const\* const ; à GetData) OCTETS\* () GetData ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD const\* GetData () const ; DWORD\* () GetData ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void\* \* () GetData const ; void\* \* () GetData ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* const ; à GetData) CString\* () GetData ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT const\* const ; à GetData) UINT\* () GetData ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD const\* const ; à GetData) WORD\* () GetData ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]  
  
##  <a name="getsize"></a>  CObArray::GetSize  
 Retourne la taille du tableau.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Notes  
 Étant donné que les index sont de base zéro, la taille est 1 supérieur le plus grand index.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::GetSize`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize () const ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize () const ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize () const ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize () const ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize () const ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize () const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>  CObArray::GetUpperBound  
 Retourne la limite supérieure en cours de ce tableau.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Index de la limite supérieure (de base zéro).  
  
### <a name="remarks"></a>Notes  
 Étant donné que les index de tableau sont de base zéro, cette fonction retourne une valeur de 1 inférieur à `GetSize`.  
  
 La condition `GetUpperBound( )` = -1 indique que le tableau ne contient aucun élément.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::GetUpperBound`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () const ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () const ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () const ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () const ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () const ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]  
  
##  <a name="insertat"></a>  CObArray::InsertAt  
 Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    CObject* newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CObArray* pNewArray);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entiers qui peut être supérieur à la valeur retournée par `GetUpperBound`.  
  
 *newElement*  
 Le `CObject` pointeur est placé dans ce tableau. Un *newElement* de valeur NULL est autorisée.  
  
 *nCount*  
 Le nombre de fois où que cet élément doit être inséré (1 par défaut).  
  
 *nStartIndex*  
 Un index d’entiers qui peut être supérieur à la valeur retournée par `GetUpperBound`.  
  
 *pNewArray*  
 Un autre tableau qui contient les éléments à ajouter à ce tableau.  
  
### <a name="remarks"></a>Notes  
 La première version de `InsertAt` insère un élément (ou plusieurs copies d’un élément) à l’index spécifié dans un tableau. Dans le processus, il se déplace (en augmentant l’index) l’élément existant à cet index et il se déplace tous les éléments au-dessus de lui.  
  
 La deuxième version insère tous les éléments d’un autre `CObArray` collection, en commençant à la *nStartIndex* position.  
  
 Le `SetAt` (fonction), en revanche, remplace un élément de tableau spécifié et tous les éléments n’est pas transférée.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::InsertAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, octets** `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1) ;**<br /><br /> **throw (CMemoryException\* ) ;**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```
  
##  <a name="isempty"></a>  CObArray::IsEmpty  
 Détermine si le tableau est vide.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le tableau est vide ; sinon 0.  
  
##  <a name="operator_at"></a>  [] CObArray::operator  
 Ces opérateurs d’indice sont une alternative pratique à la `SetAt` et `GetAt` fonctions.  
  
```  
CObject*& operator[](int_ptr nindex);  
CObject* operator[](int_ptr nindex) const;  
```  
  
### <a name="remarks"></a>Notes  
 Le premier opérateur, appelée pour les tableaux qui ne sont pas **const**, peut être utilisée sur la droite (r-value) ou la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour **const** tableaux, peut être utilisé uniquement sur la droite.  
  
 La version Debug de la bibliothèque déclare si l’indice (soit sur le côté gauche ou droit d’une instruction d’assignation) est hors limites.  
  
 Le tableau suivant présente les autres opérateurs qui sont similaires aux `CObArray::operator []`.  
  
|Classe|Opérateur|  
|-----------|--------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**[] Octets &, opérateur (int_ptr** `nindex`  **\);**<br /><br /> **Opérateur BYTE [] (int_ptr** `nindex`  **\) const ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**[] DWORD &, opérateur (int_ptr** `nindex`  **\);**<br /><br /> **DWORD operator [] (int_ptr** `nindex`  **\) const ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& operator [] (int_ptr** `nindex`  **\);**<br /><br /> **void\* operator [] (int_ptr** `nindex`  **\) const ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**[] CString &, opérateur (int_ptr** `nindex`  **\);**<br /><br /> **CString operator [] (int_ptr** `nindex`  **\) const ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**[] UINT &, opérateur (int_ptr** `nindex`  **\);**<br /><br /> **UINT, opérateur [] (int_ptr** `nindex`  **\) const ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**[] WORD &, opérateur (int_ptr** `nindex`  **\);**<br /><br /> **WORD operator [] (int_ptr** `nindex`  **\) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]  
  
##  <a name="removeall"></a>  CObArray::RemoveAll  
 Supprime tous les pointeurs de ce tableau, mais ne supprime pas réellement le `CObject` objets.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Notes  
 Si le tableau est déjà vide, la fonction fonctionne toujours.  
  
 Le `RemoveAll` fonction libère toute la mémoire utilisée pour le stockage de pointeur.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::RemoveAll`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]  
  
##  <a name="removeat"></a>  CObArray::RemoveAt  
 Supprime un ou plusieurs éléments, en commençant à un index spécifié dans un tableau.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `GetUpperBound`.  
  
 *nCount*  
 Nombre d'éléments à supprimer.  
  
### <a name="remarks"></a>Notes  
 Dans le processus, il se déplace vers le bas tous les éléments situés au-dessus de l’élément supprimé (s). Il décrémente le coin supérieur limite du tableau, mais ne libère pas de mémoire.  
  
 Si vous essayez de supprimer plus d’éléments contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque assertions.  
  
 Le `RemoveAt` fonction supprime le `CObject` pointeur à partir du tableau, mais il ne supprime pas l’objet lui-même.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::RemoveAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```
  
##  <a name="setat"></a>  CObArray::SetAt  
 Définit l’élément de tableau à l’index spécifié.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entier qui est supérieur ou égal à 0 et inférieure ou égale à la valeur retournée par `GetUpperBound`.  
  
 *newElement*  
 Le pointeur d’objet à insérer dans ce tableau. Une valeur NULL est autorisée.  
  
### <a name="remarks"></a>Notes  
 `SetAt` n’entraîne pas le tableau de croître. Utilisez `SetAtGrow` si vous souhaitez que le tableau à croître automatiquement.  
  
 Vous devez vous assurer que votre valeur d’index représente une position valide dans le tableau. Si elle est hors limites, la version Debug de la bibliothèque assertions.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::SetAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **, octets** `newElement` **) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, DWORD** `newElement` **) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, UINT** `newElement` **) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, WORD** `newElement` **) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```
  
##  <a name="setatgrow"></a>  CObArray::SetAtGrow  
 Définit l’élément de tableau à l’index spécifié.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndex*  
 Un index d’entier qui est supérieur ou égal à 0.  
  
 *newElement*  
 Le pointeur d’objet à ajouter à ce tableau. Une valeur NULL est autorisée.  
  
### <a name="remarks"></a>Notes  
 Le tableau s’étend automatiquement si nécessaire (autrement dit, la limite supérieure est ajustée pour prendre en compte le nouvel élément).  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::SetAtGrow`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, octets** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, DWORD** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, UINT** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, WORD** `newElement` **) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```
  
##  <a name="setsize"></a>  CObArray::SetSize  
 Établit la taille d’un tableau vide ou existant ; alloue de la mémoire si nécessaire.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 *nNewSize*  
 La nouvelle taille du tableau (nombre d’éléments). Doit être supérieur ou égal à 0.  
  
 *nGrowBy*  
 Le nombre minimal d’emplacements d’élément pour allouer si une augmentation de la taille est nécessaire.  
  
### <a name="remarks"></a>Notes  
 Si la nouvelle taille est inférieure à l’ancienne taille, puis du tableau est tronqué et de toute la mémoire inutilisée est libérée. Pour plus d’efficacité, appelez `SetSize` pour définir la taille du tableau avant de l’utiliser. Cela évite de devoir allouer et de copier le tableau chaque fois qu’un élément est ajouté.  
  
 Le *nGrowBy* paramètre affecte l’allocation de mémoire interne pendant que le tableau se développe. Son utilisation n’affecte jamais la taille du tableau comme indiqué par `GetSize` et `GetUpperBound`.  
  
 Si la taille du tableau a été augmenté, allouée de tous les nouveaux **CObject** <strong>\*</strong> pointeurs sont définies sur NULL.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CObArray::SetSize`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1) ;**<br /><br /> **throw (CMemoryException\* ) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CObArray::GetData](#getdata).  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Cstringarray, classe](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray, classe](../../mfc/reference/cptrarray-class.md)   
 [CByteArray, classe](../../mfc/reference/cbytearray-class.md)   
 [CWordArray, classe](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray, classe](../../mfc/reference/cdwordarray-class.md)
