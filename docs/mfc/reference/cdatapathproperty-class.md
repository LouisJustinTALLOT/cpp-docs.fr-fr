---
title: Classe de CDataPathProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e274a3fabf10e96aec41a92bb484f4ebcc5bf377
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955811"
---
# <a name="cdatapathproperty-class"></a>Classe de CDataPathProperty
Implémente une propriété de contrôle OLE qui peut être chargée de façon asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Construit un objet `CDataPathProperty`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Récupère le contrôle OLE asynchrone associé le `CDataPathProperty` objet.|  
|[CDataPathProperty::GetPath](#getpath)|Récupère le chemin d’accès de la propriété.|  
|[CDataPathProperty::Open](#open)|Démarre le chargement de la propriété asynchrone du contrôle ActiveX (OLE) associé.|  
|[CDataPathProperty::ResetData](#resetdata)|Appels `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur qui ont changé, les propriétés du contrôle.|  
|[CDataPathProperty::SetControl](#setcontrol)|Définit le contrôle ActiveX (OLE) asynchrone associé à la propriété.|  
|[CDataPathProperty::SetPath](#setpath)|Définit le chemin d’accès de la propriété.|  
  
## <a name="remarks"></a>Notes  
 Les propriétés asynchrones sont chargées après le lancement synchrone.  
  
 La classe `CDataPathProperty` est dérivée de `CAysncMonikerFile`. Pour implémenter des propriétés asynchrones dans vos contrôles OLE, dérivez une classe de `CDataPathProperty`et remplacez [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Pour plus d’informations sur l’utilisation de monikers asynchrones et les contrôles ActiveX dans les applications Internet, consultez les articles suivants :  
  
- [Internet premières étapes : Les contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet premières étapes : Les Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 Construit un objet `CDataPathProperty`.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pControl*  
 Un pointeur vers l’objet de contrôle OLE à associer à ce `CDataPathProperty` objet.  
  
 *lpszPath*  
 Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, faites précéder `file://` pour le chemin d’accès.  
  
### <a name="remarks"></a>Notes  
 Le `COleControl` objet pointé par `pControl` est utilisé par `Open` et récupérés par les classes dérivées. Si *pControl* est **NULL**, le contrôle utilisé avec `Open` doit être défini avec `SetControl`. Si `lpszPath` est **NULL**, vous pouvez passer dans le chemin d’accès via `Open` ou définissez-la avec `SetPath`.  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 Appelez cette fonction membre pour récupérer le `COleControl` objet associé à la `CDataPathProperty` objet.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le contrôle OLE associé le `CDataPathProperty` objet. **NULL** si pas de contrôle est associé.  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 Appelez cette fonction membre pour récupérer le chemin d’accès, définie lorsque le `CDataPathProperty` objet a été construit, ou spécifié dans `Open`, ou spécifié dans un appel précédent à la `SetPath` fonction membre.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le chemin d’accès à la propriété proprement dite. Peut être vide si aucun chemin d’accès n’a été spécifié.  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 Appelez cette fonction membre pour lancer le chargement de la propriété asynchrone du contrôle associé.  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pControl*  
 Un pointeur vers l’objet de contrôle OLE à associer à ce `CDataPathProperty` objet.  
  
 *pError*  
 Un pointeur vers une exception de fichier. En cas d’erreur, sera définie à la cause.  
  
 *lpszPath*  
 Le chemin d’accès, qui peut être absolu ou relatif, utilisé pour créer un moniker asynchrone qui fait référence à l’emplacement absolu réel de la propriété. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, faites précéder `file://` pour le chemin d’accès.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La fonction tente d’obtenir le `IBindHost` interface à partir du contrôle.  
  
 Avant d’appeler `Open` sans un chemin d’accès, la valeur de chemin d’accès de la propriété doit être définie. Cela est possible lorsque l’objet est construit, ou en appelant le `SetPath` fonction membre.  
  
 Avant d’appeler `Open` sans contrôle, un contrôle ActiveX (anciennement contrôle OLE) peut être associé à l’objet. Cela est possible lorsque l’objet est construit, ou en appelant `SetControl`.  
  
 Toutes les surcharges de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) sont également disponibles à partir de `CDataPathProperty`.  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 Appelez cette fonction pour obtenir `CAsyncMonikerFile::OnDataAvailable` pour notifier au conteneur que les propriétés de contrôle ont été modifiés, et toutes les informations chargées de façon asynchrone ne sont plus utiles.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Notes  
 Ouverture doit être redémarré. Classes dérivées peuvent substituer cette fonction pour différentes valeurs par défaut.  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 Appelez cette fonction membre pour associer un contrôle OLE asynchrone avec le `CDataPathProperty` objet.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Paramètres  
 *pControl*  
 Pointeur vers le contrôle OLE asynchrone à associer à la propriété.  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 Appelez cette fonction membre pour définir le chemin d’accès de la propriété.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszPath*  
 Un chemin d’accès, qui peut être absolu ou relatif à la propriété qui est chargée de façon asynchrone. `CDataPathProperty` utilise des URL, pas les noms de fichiers. Si vous souhaitez un `CDataPathProperty` de l’objet d’un fichier, faites précéder `file://` pour le chemin d’accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Image de l’exemple MFC](../../visual-cpp-samples.md)   
 [Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile, classe](../../mfc/reference/casyncmonikerfile-class.md)
