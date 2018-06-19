---
title: Classe de CStringData | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187892b74536de47079324d90bb21b2569e00498
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363569"
---
# <a name="cstringdata-class"></a>Classe de CStringData
Cette classe représente les données d’un objet string.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct CStringData
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddRef](#addref)|Incrémente le décompte de références de l’objet de données de chaîne.|  
|[data](#data)|Récupère les données de caractères d’un objet string.|  
|[IsLocked](#islocked)|Détermine si la mémoire tampon de l’objet de la chaîne associée est verrouillée.|  
|[IsShared](#isshared)|Détermine si la mémoire tampon de l’objet de la chaîne associée est partagée.|  
|[verrou](#lock)|Verrouille la mémoire tampon de l’objet de chaîne associées.|  
|[Version release](#release)|Libère l’objet de la chaîne spécifiée.|  
|[déverrouiller](#unlock)|Déverrouille la mémoire tampon de l’objet de chaîne associées.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Longueur des données allouées en `XCHAR`s (pas y compris le caractère null de fin)|  
|[nDataLength](#ndatalength)|Longueur de données actuellement utilisées dans `XCHAR`s (pas y compris le caractère null de fin)|  
|[nRefs](#nrefs)|Le décompte de références en cours de l’objet.|  
|[pStringMgr](#pstringmgr)|Pointeur vers le Gestionnaire de chaîne de cet objet de chaîne.|  
  
## <a name="remarks"></a>Notes  
 Cette classe doit uniquement être utilisée par les développeurs qui implémentent des gestionnaires de chaîne personnalisée. Pour plus d’informations sur les gestionnaires de chaîne personnalisée, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Cette classe encapsule les différents types d’informations et données associées à un objet de chaîne supérieur, tel que [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), ou [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objets. Chaque objet de chaîne supérieure contient un pointeur vers son associé `CStringData` objet, en permettant à plusieurs objets de chaîne pointer vers le même objet de données de chaîne. Cette relation est représentée par le nombre de références ( `nRefs`) de la `CStringData` objet.  
  
> [!NOTE]
>  Dans certains cas, un type de chaîne (tel que **CFixedString**) partagent pas un objet de données de chaîne avec plus d’un objet de chaîne plus élevé. Pour plus d’informations, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Ces données se compose de :  
  
-   Le Gestionnaire de mémoire (de type [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) de la chaîne.  
  
-   La longueur actuelle ( [nDataLength](#ndatalength)) de la chaîne.  
  
-   La durée allouée ( [nAllocLength](#nalloclength)) de la chaîne. Pour des raisons de performances, il peut être différent de la longueur de chaîne en cours  
  
-   Le décompte de références en cours ( [nRefs](#nrefs)) de la `CStringData` objet. Cette valeur est utilisée pour déterminer le nombre d’objets chaîne partagent le même `CStringData` objet.  
  
-   La mémoire tampon caractère réel ( [données](#data)) de la chaîne.  
  
    > [!NOTE]
    >  La mémoire tampon de caractères réelle de l’objet string est allouée par le Gestionnaire de chaîne et est ajoutée à la `CStringData` objet.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsimpstr.h  
  
##  <a name="addref"></a>  CStringData::AddRef  
 Incrémente le décompte de références de l’objet string.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Notes  
 Incrémente le décompte de références de l’objet string.  
  
> [!NOTE]
>  N’appelez pas cette méthode sur une chaîne avec un nombre négatif de référence, car un nombre négatif indique que la mémoire tampon de chaîne est verrouillé.  
  
##  <a name="data"></a>  CStringData::data  
 Retourne un pointeur vers la mémoire tampon de caractères d’un objet string.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la mémoire tampon de caractères de l’objet string.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour retourner la mémoire tampon de caractères en cours de l’objet de chaîne associées.  
  
> [!NOTE]
>  Ce tampon n’est pas alloué par le `CStringData` objet mais par le Gestionnaire de chaîne si nécessaire. Lors de l’allocation, la mémoire tampon est ajoutée à l’objet de données de chaîne.  
  
##  <a name="islocked"></a>  CStringData::IsLocked  
 Détermine si la mémoire tampon de caractères est verrouillé.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si la mémoire tampon est verrouillée ; sinon **false**.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour déterminer si la mémoire tampon de caractères d’un objet string est actuellement verrouillé.  
  
##  <a name="isshared"></a>  CStringData::IsShared  
 Détermine si la mémoire tampon de caractères est partagé.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si la mémoire tampon est partagée ; sinon **false**.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour déterminer si la mémoire tampon de caractères d’un objet de données de chaîne est partagé entre plusieurs objets de chaîne.  
  
##  <a name="lock"></a>  CStringData::Lock  
 Verrouille la mémoire tampon de caractères de l’objet de chaîne associées.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour verrouiller la mémoire tampon de caractères de l’objet de données de chaîne. Verrouillage et déverrouillage sont utilisé lorsqu’un accès direct à la mémoire tampon de caractères est requise par le développeur. Un bon exemple de verrouillage est illustré par le [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) méthodes de `CSimpleStringT`.  
  
> [!NOTE]
>  Une mémoire tampon de caractères peut uniquement être verrouillé si la mémoire tampon n’est pas partagée entre les objets de chaîne supérieur.  
  
##  <a name="nalloclength"></a>  CStringData::nAllocLength  
 Longueur de la mémoire tampon caractère alloué.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Notes  
 Stocke la longueur de la mémoire tampon de données allouées en `XCHAR`s (pas y compris le caractère null de fin).  
  
##  <a name="ndatalength"></a>  CStringData::nDataLength  
 Longueur actuelle de l’objet string.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Notes  
 Stocke la longueur de données actuellement utilisées dans `XCHAR`s (pas y compris le caractère null de fin).  
  
##  <a name="nrefs"></a>  CStringData::nRefs  
 Nombre de références de l’objet de données de chaîne.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Notes  
 Stocke le nombre de références de l’objet de données de chaîne. Ce nombre indique le nombre d’objets de chaîne supérieur qui sont associés à l’objet de données de chaîne. Une valeur négative indique que l’objet de données de chaîne est actuellement verrouillé.  
  
##  <a name="pstringmgr"></a>  CStringData::pStringMgr  
 Le Gestionnaire de mémoire de l’objet de chaîne associées.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Notes  
 Stocke le Gestionnaire de mémoire pour l’objet de chaîne associées. Pour plus d’informations sur les chaînes et les gestionnaires de mémoire, consultez [gestion de la mémoire et CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>  CStringData::Release  
 Décrémente le décompte de références de l’objet de données de chaîne.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour décrémenter le décompte de références, la libération de la `CStringData` structure si le décompte de références atteint zéro. Cela est généralement effectué lorsqu’un objet string est supprimé et par conséquent n’a plus besoin référencer l’objet de données de chaîne.  
  
 Par exemple, appelez le code suivant `CStringData::Release` pour l’objet de données de chaîne associé `str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>  CStringData::Unlock  
 Déverrouille la mémoire tampon de caractères de l’objet de chaîne associées.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour déverrouiller la mémoire tampon de caractères de l’objet de données de chaîne. Une fois qu’une mémoire tampon est déverrouillée, il est partageable et référence peut être comptée.  
  
> [!NOTE]
>  Chaque appel à `Lock` doit correspondre à un appel correspondant à `Unlock`.  
  
 Verrouillage et déverrouillage sont utilisé lorsque le développeur doit s’assurer que les données de chaîne ne soit ne pas partagée. Un bon exemple de verrouillage est illustré par le [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) et [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) méthodes de `CSimpleStringT`.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


