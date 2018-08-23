---
title: CBulkRowset, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e741055950449ea07c719cf6cd4c33a34d6f43b3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571557"
---
# <a name="cbulkrowset-class"></a>CBulkRowset, classe
Récupère et manipule des lignes à traiter les données en bloc en récupérant plusieurs handles de ligne avec un seul appel.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
### <a name="parameters"></a>Paramètres  
 *TAccessor*  
 Classe d’accesseur.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddRefRows](#addrefrows)|Incrémente le décompte de références.|  
|[CBulkRowset](#cbulkrowset)|Constructeur.|  
|[MoveFirst](#movefirst)|Récupère la première ligne de données, en effectuant une nouvelle extraction en bloc si nécessaire.|  
|[MoveLast](#movelast)|Passe à la dernière ligne.|  
|[MoveNext](#movenext)|Récupère la ligne suivante de données.|  
|[MovePrev](#moveprev)|Se déplace vers la ligne précédente.|  
|[MoveToBookmark](#movetobookmark)|Extrait la ligne marquée par un signet ou la ligne à l’offset spécifié à partir de ce signet.|  
|[MoveToRatio](#movetoratio)|Extrait les lignes à partir d’un emplacement de fractions de seconde dans l’ensemble de lignes.|  
|[ReleaseRows](#releaserows)|Définit la ligne actuelle (`m_nCurrentRow`) à zéro et les versions de toutes les lignes.|  
|[SetRows](#setrows)|Définit le nombre de handles de ligne doivent être récupérées à un seul appel.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `CBulkRowset` classe.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  

## <a name="addrefrows"></a> CBulkRowset::AddRefRows
Appels [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619\(v=vs.85\)) pour incrémenter le décompte de références pour toutes les lignes actuellement récupérées à partir de l’ensemble de lignes en bloc.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddRefRows() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard. 
  
## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset
Crée un `CBulkRowset` de l’objet et affecte le nombre de lignes par défaut 10.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CBulkRowset();  
```  

## <a name="movefirst"></a> CBulkRowset::MoveFirst
Récupère la première ligne de données.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveFirst() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.

## <a name="movelast"></a> CBulkRowset::MoveLast
Passe à la dernière ligne.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveLast() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="movenext"></a> CBulkRowset::MoveNext
Récupère la ligne suivante de données.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveNext() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard. Lorsque la fin de l’ensemble de lignes a été atteinte, retourne DB_S_ENDOFROWSET. 

## <a name="moveprev"></a> CBulkRowset::MovePrev
Se déplace vers la ligne précédente.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MovePrev() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark
Extrait la ligne marquée par un signet ou la ligne à l’offset spécifié (*lSkip*) à partir de ce signet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark, 
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Signet*  
 [in] Un signet est l’emplacement à partir duquel vous souhaitez extraire des données.  
  
 *lSkip*  
 [in] Le nombre de lignes à partir du signet à la ligne cible. Si *lSkip* est égal à zéro, la première ligne extraite est la ligne marquée par un signet. Si *lSkip* est 1, la première ligne extraite est la ligne après la ligne marquée par un signet. Si *lSkip* est -1, la première ligne extraite est la ligne avant la ligne marquée par un signet.  
  
### <a name="return-value"></a>Valeur de retour  
 Consultez [IRowset::GetData](/previous-versions/windows/desktop/ms716988\(v=vs.85\)) dans le *de référence du programmeur OLE DB*. 

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio
Extrait les lignes à partir d’un emplacement de fractions de seconde dans l’ensemble de lignes.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator, 
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nNumerator*  
 [in] Le numérateur est utilisé pour déterminer la position décimale à partir de laquelle extraire des données.  
  
 *nDenominator*  
 [in] Le dénominateur permet de déterminer la position décimale à partir de laquelle extraire des données.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 `MoveToRatio` extrait les lignes à peu près en fonction de la formule suivante :  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 Où `RowsetSize` est la taille de l’ensemble de lignes, mesurée en lignes. La précision de cette formule varie selon le fournisseur spécifique. Pour plus d’informations, consultez [IRowsetScroll::GetRowsAtRatio](/previous-versions/windows/desktop/ms709602\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.   

## <a name="releaserows"></a> CBulkRowset::ReleaseRows
Appels [IRowset::ReleaseRows](/previous-versions/windows/desktop/ms719771\(v=vs.85\)) pour décrémenter le décompte de références pour toutes les lignes actuellement récupérées à partir de l’ensemble de lignes en bloc.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReleaseRows() throw();   
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  

## <a name="setrows"></a> CBulkRowset::SetRows
Définit le nombre de descripteurs de lignes récupérées par chaque appel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void SetRows(DBROWCOUNT nRows) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nRows*  
 [in] La nouvelle taille de l’ensemble de lignes (nombre de lignes).  
  
### <a name="remarks"></a>Notes  
 Si vous appelez cette fonction, il doit être avant l’ouverture de l’ensemble de lignes.
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)