---
title: Classe de COleSafeArray | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
dev_langs:
- C++
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b85c64837f9bc7a0c8c1873f434855d77c01fb1b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041631"
---
# <a name="colesafearray-class"></a>Classe de COleSafeArray
Classe pour utiliser des tableaux de type et de dimension arbitraires.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleSafeArray::COleSafeArray](#colesafearray)|Construit un objet `COleSafeArray`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleSafeArray::AccessData](#accessdata)|Récupère un pointeur vers les données de tableau.|  
|[COleSafeArray::AllocData](#allocdata)|Alloue la mémoire pour le tableau.|  
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Alloue la mémoire pour le descripteur de tableau sécurisé.|  
|[COleSafeArray::Attach](#attach)|Donne le contrôle existants **VARIANT** de tableau pour le `COleSafeArray` objet.|  
|[COleSafeArray::Clear](#clear)|Libère toutes les données sous-jacentes **variante**.|  
|[COleSafeArray::Copy](#copy)|Crée une copie d’un tableau existant.|  
|[COleSafeArray::Create](#create)|Crée un tableau sécurisé.|  
|[COleSafeArray::CreateOneDim](#createonedim)|Crée une dimension `COleSafeArray` objet.|  
|[COleSafeArray::Destroy](#destroy)|Détruit un tableau existant.|  
|[COleSafeArray::DestroyData](#destroydata)|Supprime les données dans un tableau sécurisé.|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Détruit un descripteur d’un tableau sécurisé.|  
|[COleSafeArray::Detach](#detach)|Détache le **VARIANT** de tableau à partir de la `COleSafeArray` (de sorte que les données ne seront pas libérées) de l’objet.|  
|[COleSafeArray::GetByteArray](#getbytearray)|Copie le contenu du tableau sécurisé dans un [CByteArray](../../mfc/reference/cbytearray-class.md).|  
|[COleSafeArray::GetDim](#getdim)|Retourne le nombre de dimensions du tableau.|  
|[COleSafeArray::GetElement](#getelement)|Récupère un seul élément du tableau sécurisé.|  
|[COleSafeArray::GetElemSize](#getelemsize)|Retourne la taille, en octets, d’un seul élément dans un tableau sécurisé.|  
|[COleSafeArray::GetLBound](#getlbound)|Retourne la limite inférieure d’une dimension d’un tableau sécurisé.|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Retourne le nombre d’éléments dans la dimension `COleSafeArray` objet.|  
|[COleSafeArray::GetUBound](#getubound)|Retourne la limite supérieure d’une dimension d’un tableau sécurisé.|  
|[COleSafeArray::Lock](#lock)|Incrémente le nombre de verrous d’un tableau et place un pointeur vers les données de tableau dans le descripteur du tableau.|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Retourne un pointeur vers l’élément indexé.|  
|[COleSafeArray::PutElement](#putelement)|Affecte un élément unique dans le tableau.|  
|[COleSafeArray::Redim](#redim)|Modifie la limite moins significative (le plus à droite) d’un tableau sécurisé.|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Modifie le nombre d’éléments dans une dimension `COleSafeArray` objet.|  
|[COleSafeArray::UnaccessData](#unaccessdata)|Décrémente le verrou comptage d’un tableau et invalide le pointeur récupéré par `AccessData`.|  
|[COleSafeArray::Unlock](#unlock)|Décrémente le nombre de verrous d’un tableau afin qu’il peut être libérée ou redimensionné.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Accède à sous-jacent **VARIANT** structure de le `COleSafeArray` objet.|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Accède à sous-jacent **VARIANT** structure de le `COleSafeArray` objet.|  
|[COleSafeArray::operator =](#operator_eq)|Copie les valeurs dans une `COleSafeArray` objet ( **SAFEARRAY**, **VARIANT**, `COleVariant`, ou `COleSafeArray` tableau).|  
|[COleSafeArray::operator ==](#operator_eq_eq)|Compare deux tableaux variants ( **SAFEARRAY**, **variante**, `COleVariant`, ou `COleSafeArray` tableaux).|  
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Renvoie le contenu d’un `COleSafeArray` objet dans le contexte de dump.|  
  
## <a name="remarks"></a>Notes  
 `COleSafeArray` dérive de l’OLE **VARIANT** structure. OLE **SAFEARRAY** fonctions membres sont disponibles via `COleSafeArray`, ainsi que comme un ensemble de fonctions membres spécifiquement conçu pour les tableaux unidimensionnels d’octets.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h  
  
##  <a name="accessdata"></a>  COleSafeArray::AccessData  
 Récupère un pointeur vers les données de tableau.  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppvData*  
 Pointeur vers un pointeur vers les données de tableau.  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="allocdata"></a>  COleSafeArray::AllocData  
 Alloue la mémoire pour un tableau sécurisé.  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor  
 Alloue la mémoire pour le descripteur d’un tableau sécurisé.  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDims*  
 Nombre de dimensions dans le tableau sécurisé.  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="attach"></a>  COleSafeArray::Attach  
 Permet de contrôler les données dans un fichier **VARIANT** de tableau pour le `COleSafeArray` objet.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 *varSrc*  
 A **VARIANT** objet. Le *varSrc* le paramètre doit avoir la [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**.  
  
### <a name="remarks"></a>Notes  
 La source de **VARIANT**de type est défini sur `VT_EMPTY`. Cette fonction efface les données de tableau en cours, le cas échéant.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="clear"></a>  COleSafeArray::Clear  
 Efface le tableau sécurisé.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Notes  
 La fonction efface un tableau sécurisé en définissant le `VARTYPE` de l’objet à `VT_EMPTY`. Le contenu actuel est libéré et que le tableau est libéré.  
  
##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray  
 Construit un objet `COleSafeArray`.  
  
```  
COleSafeArray();

 
COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

 
COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);  
  
COleSafeArray(const COleSafeArray& saSrc);  
COleSafeArray(const VARIANT& varSrc);  
  COleSafeArray(LPCVARIANT pSrc);  
COleSafeArray(const COleVariant& varSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 *saSrc*  
 Existant `COleSafeArray` objet ou **SAFEARRAY** à copier dans le nouveau `COleSafeArray` objet.  
  
 *vtSrc*  
 Le **VARTYPE** du nouveau `COleSafeArray` objet.  
  
 *psaSrc*  
 Un pointeur vers un **SAFEARRAY** à copier dans le nouveau `COleSafeArray` objet.  
  
 *varSrc*  
 Existant **VARIANT** ou `COleVariant` à copier dans le nouvel objet `COleSafeArray` objet.  
  
 *pSrc*  
 Un pointeur vers un **VARIANT** à copier dans le nouvel objet `COleSafeArray` objet.  
  
### <a name="remarks"></a>Notes  
 Toutes ces constructeurs créent de nouveaux `COleSafeArray` objets. S’il n’existe aucun paramètre, vide `COleSafeArray` objet est créé ( `VT_EMPTY`). Si le `COleSafeArray` est copié à partir d’un autre tableau dont [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) est appelée implicitement (un `COleSafeArray`, `COleVariant`, ou **VARIANT**), la **VARTYPE** de le tableau source est conservé et ne doive pas être spécifié. Si le `COleSafeArray` est copié à partir d’un autre tableau dont **VARTYPE** n’est pas connu ( **SAFEARRAY**), la **VARTYPE** doit être spécifié dans le *vtSrc* paramètre.  
  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="copy"></a>  COleSafeArray::Copy  
 Crée une copie d’un tableau sécurisé existant.  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppsa*  
 Pointeur vers un emplacement dans lequel retourner le nouveau descripteur de tableau.  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="create"></a>  COleSafeArray::Create  
 Alloue et initialise les données pour le tableau.  
  
```  
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    DWORD* rgElements);

 
void Create(
    VARTYPE vtSrc,  
    DWORD dwDims,  
    SAFEARRAYBOUND* rgsabounds);
```  
  
### <a name="parameters"></a>Paramètres  
 *vtSrc*  
 Le type de base du tableau (autrement dit, le **VARTYPE** de chaque élément du tableau). Le **VARTYPE** est limité à un sous-ensemble des types variants. Ni le **VT_ARRAY** ni le **VT_BYREF** indicateur peut être défini. **VT_EMPTY** et **VT_NULL** ne sont pas des types de base valides pour le tableau. Tous les autres types sont autorisés.  
  
 *dwDims*  
 Nombre de dimensions dans le tableau. Cela peut être modifié une fois que le tableau est créé avec [Redim](#redim).  
  
 *rgElements*  
 Pointeur vers un tableau du nombre d’éléments pour chaque dimension du tableau.  
  
 *rgsabounds*  
 Pointeur vers un vecteur de limites (une pour chaque dimension) à allouer pour le tableau.  
  
### <a name="remarks"></a>Notes  
 Cette fonction efface les données de tableau en cours si nécessaire. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim  
 Crée une nouvelle dimension `COleSafeArray` objet.  
  
```  
void CreateOneDim(
    VARTYPE vtSrc,  
    DWORD dwElements,  
    const void* pvSrcData = NULL,  
    long nLBound = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *vtSrc*  
 Le type de base du tableau (autrement dit, le **VARTYPE** de chaque élément du tableau).  
  
 *dwElements*  
 Nombre d’éléments dans le tableau. Cela peut être modifié une fois que le tableau est créé avec [ResizeOneDim](#resizeonedim).  
  
 *pvSrcData*  
 Pointeur vers les données à copier dans le tableau.  
  
 *nLBound*  
 La limite inférieure du tableau.  
  
### <a name="remarks"></a>Notes  
 La fonction alloue et initialise les données pour le tableau, en copiant les données spécifiées si le pointeur *pvSrcData* n’est pas **NULL**.  
  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="destroy"></a>  COleSafeArray::Destroy  
 Détruit un descripteur de tableau existant et toutes les données dans le tableau.  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>Notes  
 Si les objets sont stockés dans le tableau, chaque objet est libérée. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydata"></a>  COleSafeArray::DestroyData  
 Supprime toutes les données dans un tableau sécurisé.  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>Notes  
 Si les objets sont stockés dans le tableau, chaque objet est libérée. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor  
 Détruit un descripteur d’un tableau sécurisé.  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="detach"></a>  COleSafeArray::Detach  
 Détache le **VARIANT** les données à partir de la `COleSafeArray` objet.  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Sous-jacent **VARIANT** valeur dans le `COleSafeArray` objet.  
  
### <a name="remarks"></a>Notes  
 La fonction détache les données dans un tableau sécurisé en définissant le [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) de l’objet à `VT_EMPTY`. Il incombe l’appelant de libérer le tableau en appelant la fonction Windows [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835).  
  
 En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleSafeArray::PutElement](#putelement).  
  
##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray  
 Copie le contenu du tableau sécurisé dans un `CByteArray`.  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Paramètres  
 *Octets*  
 Une référence à un [CByteArray](../../mfc/reference/cbytearray-class.md) objet.  
  
##  <a name="getdim"></a>  COleSafeArray::GetDim  
 Retourne le nombre de dimensions dans le `COleSafeArray` objet.  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de dimensions dans le tableau sécurisé.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="getelement"></a>  COleSafeArray::GetElement  
 Récupère un seul élément du tableau sécurisé.  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>Paramètres  
 *rgIndices*  
 Pointeur vers un tableau d'index pour chaque dimension du tableau.  
  
 *pvData*  
 Pointeur vers l’emplacement pour placer l’élément du tableau.  
  
### <a name="remarks"></a>Notes  
 Cette fonction appelle automatiquement les fonctions windows `SafeArrayLock` et `SafeArrayUnlock` avant et après la récupération de l’élément. Si l’élément de données est une chaîne, un objet ou un variant, la fonction de copie l’élément dans la méthode correcte. Le paramètre *pvData* doit pointer vers une mémoire tampon insuffisante pour contenir l’élément.  
  
 En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize  
 Récupère la taille d’un élément dans un `COleSafeArray` objet.  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille, en octets, des éléments d’un tableau sécurisé.  
  
##  <a name="getlbound"></a>  COleSafeArray::GetLBound  
 Retourne la limite inférieure d’une dimension d’un `COleSafeArray` objet.  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDim*  
 La dimension du tableau pour lequel obtenir la limite inférieure.  
  
 *pLBound*  
 Pointeur vers l’emplacement pour retourner la limite inférieure.  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize  
 Retourne le nombre d’éléments dans la dimension `COleSafeArray` objet.  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le tableau unidimensionnel de sécurité.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="getubound"></a>  COleSafeArray::GetUBound  
 Retourne la limite supérieure d’une dimension d’un tableau sécurisé.  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDim*  
 La dimension du tableau pour lequel obtenir la limite supérieure.  
  
 *pUBound*  
 Pointeur vers l’emplacement pour retourner la limite supérieure.  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="lock"></a>  COleSafeArray::Lock  
 Incrémente le nombre de verrous d’un tableau et le place un pointeur vers les données de tableau dans le descripteur du tableau.  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>Notes  
 En cas d’erreur, elle lève une [COleException](../../mfc/reference/coleexception-class.md).  
  
 Le pointeur dans le descripteur de tableau est valide tant que `Unlock` est appelée. Les appels à `Lock` peuvent être imbriqués ; un nombre égal d’appels à `Unlock` sont requis.  
  
 Un tableau ne peut pas être supprimé lorsqu’il est verrouillé.  
  
##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT  
 Appelez cet opérateur de cast pour accéder à l’objet sous-jacent **VARIANT** structure pour ce `COleSafeArray` objet.  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT  
 Appelez cet opérateur de cast pour accéder à l’objet sous-jacent **VARIANT** structure pour ce `COleSafeArray` objet.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Notes  
 Notez que si vous modifiez la valeur dans la **VARIANT** structure accédé par le pointeur retourné par cette fonction modifie la valeur de ce `COleSafeArray` objet.  
  
##  <a name="operator_eq"></a>  COleSafeArray::operator =  
 Ces opérateurs d’assignation surchargés copiez la valeur source dans cette `COleSafeArray` objet.  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>Notes  
 Une brève description de chaque opérateur suit :  
  
- **opérateur = (** *saSrc* **)** copie existant `COleSafeArray` objet dans cet objet.  
  
- **opérateur = (** *varSrc ***)** copie existant **VARIANT** ou `COleVariant` tableau dans cet objet.  
  
- **opérateur = (** `pSrc` **)** Copies le **VARIANT** objet de tableau accédé en `pSrc` dans cet objet.  
  
##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==  
 Cet opérateur compare deux tableaux ( **SAFEARRAY**, **VARIANT**, `COleVariant`, ou `COleSafeArray` tableaux) et retourne zéro si elles sont égales ; sinon, 0.  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
Opérateur CDumpContext & AFXAPI << (CDumpContext & contrôleur de domaine,  
    COleSafeArray & saSrc) ;
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (long * rgIndices,  
    void ** ppvData) ;
```  
  
### Parameters  
 *rgIndices*  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 *ppvData*  
 On return, pointer to the element identified by the values in *rgIndices*.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (long * rgIndices,  
    void * pvData) ;
```  
  
### Parameters  
 *rgIndices*  
 Pointer to an array of indexes for each dimension of the array.  
  
 *pvData*  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and **VT_BSTR** variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
Redim void (SAFEARRAYBOUND * psaboundNew) ;
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements) ;
```  
  
### Parameters  
 *dwElements*  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData() ;
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock() ;
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)
