---
title: Classe de COleDataObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e5beccea254db8c7db6b6f52fee6c5d3021da71
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038330"
---
# <a name="coledataobject-class"></a>Classe de COleDataObject
Utilisée dans les transferts de données pour récupérer des données dans divers formats depuis le Presse-papiers, par glisser-déposer ou depuis un élément OLE incorporé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|Construit un objet `COleDataObject`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|Attache l’objet de données OLE spécifié à la `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Attache l’objet de données qui se trouve sur le Presse-papiers.|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Prépare pour un ou plus ultérieures `GetNextFormat` appels.|  
|[COleDataObject::Detach](#detach)|Détache associé `IDataObject` objet.|  
|[COleDataObject::GetData](#getdata)|Copie des données à partir de l’objet de données attaché OLE dans un format spécifié.|  
|[COleDataObject::GetFileData](#getfiledata)|Copie des données à partir de l’objet de données attaché OLE dans un `CFile` pointeur dans le format spécifié.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Copie des données à partir de l’objet de données attaché OLE dans un `HGLOBAL` dans le format spécifié.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Retourne le format de données suivant disponible.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Vérifie si les données sont disponibles dans un format spécifié.|  
|[COleDataObject::Release](#release)|Détache et libère associé `IDataObject` objet.|  
  
## <a name="remarks"></a>Notes  
 `COleDataObject` ne dispose pas d’une classe de base.  
  
 Ces types de transferts de données incluent une source et une destination. La source de données est implémentée en tant qu’objet de la [COleDataSource](../../mfc/reference/coledatasource-class.md) classe. Chaque fois qu’une application de destination contient des données supprimées qu’il contient ou qu’il est invitée à effectuer une opération de collage depuis le Presse-papiers, un objet de la `COleDataObject` classe doit être créée.  
  
 Cette classe vous permet de déterminer si les données existent dans un format spécifié. Vous pouvez également énumérer les formats de données disponibles ou vérifier si un format donné est disponible et récupérer les données dans le format par défaut. Récupération de l’objet peut être effectuée de différentes façons, notamment l’utilisation d’un [CFile](../../mfc/reference/cfile-class.md), un `HGLOBAL`, ou un **STGMEDIUM** structure.  
  
 Pour plus d’informations, consultez la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure dans le SDK Windows.  
  
 Pour plus d’informations sur l’utilisation des objets de données dans votre application, consultez l’article [des objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `COleDataObject`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="attach"></a>  COleDataObject::Attach  
 Appelez cette fonction pour associer le `COleDataObject` objet avec un objet de données OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *objet lpDataObject*  
 Pointe vers un objet de données OLE.  
  
 *bAutoRelease*  
 **TRUE** si l’objet de données OLE doit être libérée lorsque la `COleDataObject` objet est détruite ; sinon **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) dans le Kit de développement logiciel Windows.  
  
##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard  
 Appelez cette fonction pour attacher l’objet de données qui est actuellement dans le Presse-papiers pour le `COleDataObject` objet.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Appel de cette fonction de verrouille le Presse-papiers jusqu'à ce que cet objet de données est libéré. L’objet de données est libéré dans le destructeur de la `COleDataObject`. Pour plus d’informations, consultez [ouverture du Presse-papiers](http://msdn.microsoft.com/library/windows/desktop/ms649048) et [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) dans la documentation de Win32.  
  
##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats  
 Appelez cette fonction pour préparer les appels suivants à `GetNextFormat` pour récupérer une liste des formats de données à partir de l’élément.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Notes  
 Après un appel à `BeginEnumFormats`, la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données.  
  
 Pour vérifier la disponibilité des données dans un format donné, utilisez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) dans le Kit de développement logiciel Windows.  
  
##  <a name="coledataobject"></a>  COleDataObject::COleDataObject  
 Construit un objet `COleDataObject`.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Notes  
 Un appel à [COleDataObject::Attach](#attach) ou [COleDataObject::AttachClipboard](#attachclipboard) doivent être effectuées avant d’appeler d’autres `COleDataObject` fonctions.  
  
> [!NOTE]
>  Étant donné que l’un des paramètres pour les gestionnaires de glisser-déplacer est un pointeur vers un `COleDataObject`, il n’est pas nécessaire d’appeler ce constructeur pour prendre en charge du glisser -déplacer.  
  
##  <a name="detach"></a>  COleDataObject::Detach  
 Appelez cette fonction pour détacher le `COleDataObject` objet à partir de l’objet de données associé OLE sans le libérer l’objet de données.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet de données OLE qui a été détachée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdata"></a>  COleDataObject::GetData  
 Appelez cette fonction pour récupérer des données à partir de l’élément dans le format spécifié.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format dans lequel les données sont à retourner. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpStgMedium*  
 Pointe vers un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure qui recevront des données.  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données sont à retourner. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="getfiledata"></a>  COleDataObject::GetFileData  
 Appelez cette fonction pour créer un `CFile` ou `CFile`-objet dérivé et récupérer des données dans le format spécifié dans un `CFile` pointeur.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format dans lequel les données sont à retourner. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données sont à retourner. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la nouvelle `CFile` ou `CFile`-dérivée objet contenant les données de cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Selon le support, les données sont stockées dans, le type réel désigné par la valeur de retour peut être `CFile`, `CSharedFile`, ou `COleStreamFile`.  
  
> [!NOTE]
>  Le `CFile` objet accédé par la valeur de retour de cette fonction est possédée par l’appelant. Il incombe à l’appelant de **supprimer** le `CFile` objet, et de fermeture du fichier.  
  
 Pour plus d’informations, consultez [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData  
 Appelez cette fonction pour allouer un bloc de mémoire globale et pour récupérer des données dans le format spécifié dans un `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format dans lequel les données sont à retourner. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format dans lequel les données sont à retourner. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du bloc de mémoire globale qui contient les données en cas de réussite ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat  
 Appelez cette fonction à plusieurs reprises pour obtenir tous les formats disponibles pour la récupération des données à partir de l’élément.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui reçoit les informations de format lors de l’appel de fonction retourne.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un autre format n’est disponible ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Après un appel à [COleDataObject::BeginEnumFormats](#beginenumformats), la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données. Utilisez ces fonctions pour répertorier les formats disponibles.  
  
 Pour vérifier la disponibilité d’un format donné, appelez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) dans le Kit de développement logiciel Windows.  
  
##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable  
 Appelez cette fonction pour déterminer si un format particulier est disponible pour la récupération des données à partir de l’élément OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de données du Presse-papiers pour être utilisé dans la structure vers laquelle pointe *lpFormatEtc*. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows natif [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui décrit le format désiré. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les données sont disponibles dans le format spécifié ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utile avant d’appeler `GetData`, `GetFileData`, ou `GetGlobalData`.  
  
 Pour plus d’informations, consultez [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>  COleDataObject::Release  
 Appelez cette fonction pour libérer la possession de la [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objet qui a été précédemment associé à la `COleDataObject` objet.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Notes  
 Le `IDataObject` a été associé à la `COleDataObject` en appelant `Attach` ou `AttachClipboard` ou explicitement par l’infrastructure. Si le `bAutoRelease` paramètre de `Attach` est **FALSE**, le `IDataObject` objet n’est pas libéré. Dans ce cas, l’appelant est responsable de la libération du `IDataObject` en appelant [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleDataSource](../../mfc/reference/coledatasource-class.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
