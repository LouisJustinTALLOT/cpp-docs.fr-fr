---
title: COleDataObject, classe | Microsoft Docs
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
ms.openlocfilehash: 67a4f03db6a7c4cf37e59e05464865016d836097
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215006"
---
# <a name="coledataobject-class"></a>COleDataObject, classe
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
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Prépare pour un ou plus suivantes `GetNextFormat` appels.|  
|[COleDataObject::Detach](#detach)|Détache associé `IDataObject` objet.|  
|[COleDataObject::GetData](#getdata)|Copie des données à partir de l’objet de données OLE attaché dans un format spécifié.|  
|[COleDataObject::GetFileData](#getfiledata)|Copie les données à partir de l’objet de données OLE attaché dans un `CFile` pointeur au format spécifié.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Copie les données à partir de l’objet de données OLE attaché dans un `HGLOBAL` au format spécifié.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Retourne le format de données suivant disponible.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Vérifie si les données sont disponibles dans un format spécifié.|  
|[COleDataObject::Release](#release)|Détache et libère associé `IDataObject` objet.|  
  
## <a name="remarks"></a>Notes  
 `COleDataObject` n’a pas d’une classe de base.  
  
 Ces types de transferts de données incluent une source et une destination. La source de données est implémentée en tant qu’objet de la [COleDataSource](../../mfc/reference/coledatasource-class.md) classe. Chaque fois qu’une application de destination a supprimé qu’il contient des données ou est invitée à effectuer une opération de collage à partir du Presse-papiers, un objet de la `COleDataObject` classe doit être créée.  
  
 Cette classe vous permet de déterminer si les données existent dans un format spécifié. Vous pouvez également énumérer les formats de données disponibles ou vérifier si un format donné est disponible et récupère ensuite les données dans le format par défaut. Récupération de l’objet est possible de différentes façons, notamment l’utilisation d’un [CFile](../../mfc/reference/cfile-class.md), un HGLOBAL, ou un `STGMEDIUM` structure.  
  
 Pour plus d’informations, consultez le [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) structure dans le SDK Windows.  
  
 Pour plus d’informations sur l’utilisation des objets de données dans votre application, consultez l’article [objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
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
 TRUE si l’objet de données OLE doit être libérée lorsque la `COleDataObject` objet est détruite ; sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) dans le SDK Windows.  
  
##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard  
 Appelez cette fonction pour attacher l’objet de données qui est actuellement dans le Presse-papiers pour le `COleDataObject` objet.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Appel de cette fonction verrouille le Presse-papiers jusqu'à ce que cet objet de données est libéré. L’objet de données est libéré dans le destructeur de la `COleDataObject`. Pour plus d’informations, consultez [ouverture du Presse-papiers](/windows/desktop/api/winuser/nf-winuser-openclipboard) et [CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) dans la documentation de Win32.  
  
##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats  
 Appelez cette fonction pour vous préparer à des appels ultérieurs à `GetNextFormat` pour récupérer une liste de formats de données à partir de l’élément.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Notes  
 Après un appel à `BeginEnumFormats`, la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données.  
  
 Pour vérifier la disponibilité des données dans un format donné, utilisez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) dans le SDK Windows.  
  
##  <a name="coledataobject"></a>  COleDataObject::COleDataObject  
 Construit un objet `COleDataObject`.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Notes  
 Un appel à [COleDataObject::Attach](#attach) ou [COleDataObject::AttachClipboard](#attachclipboard) doivent être effectuées avant d’appeler d’autres `COleDataObject` fonctions.  
  
> [!NOTE]
>  Étant donné que l’un des paramètres pour les gestionnaires de glisser-déplacer est un pointeur vers un `COleDataObject`, il est inutile d’appeler ce constructeur pour prendre en charge du glisser -déplacer.  
  
##  <a name="detach"></a>  COleDataObject::Detach  
 Appelez cette fonction pour détacher le `COleDataObject` objet à partir de l’objet de données OLE associé sans libérer l’objet de données.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet de données OLE a été détachée.  
  
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
 Le format dans lequel les données doit être retourné. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows native [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) (fonction).  
  
 *lpStgMedium*  
 Pointe vers un [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) structure qui recevra les données.  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure qui décrit le format dans lequel les données doit être retourné. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si sa valeur est NULL, les valeurs par défaut sont utilisés pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) dans le SDK Windows.  
  
##  <a name="getfiledata"></a>  COleDataObject::GetFileData  
 Appelez cette fonction pour créer un `CFile` ou `CFile`-objet dérivé et pour récupérer des données au format spécifié dans un `CFile` pointeur.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format dans lequel les données doit être retourné. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows native [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure qui décrit le format dans lequel les données doit être retourné. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si sa valeur est NULL, les valeurs par défaut sont utilisés pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le nouveau `CFile` ou `CFile`-dérivés d’objet contenant les données de cas de réussite ; sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Selon le support, les données sont stockées dans, le type réel désigné par la valeur de retour peut être `CFile`, `CSharedFile`, ou `COleStreamFile`.  
  
> [!NOTE]
>  Le `CFile` objet accédé par la valeur de retour de cette fonction est possédée par l’appelant. Il incombe à l’appelant de **supprimer** le `CFile` objet, donc fermer le fichier.  
  
 Pour plus d’informations, consultez [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) dans le SDK Windows.  
  
##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData  
 Appelez cette fonction pour allouer un bloc de mémoire globale et pour extraire des données au format spécifié dans un HGLOBAL.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format dans lequel les données doit être retourné. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows native [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure qui décrit le format dans lequel les données doit être retourné. Indiquez une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si sa valeur est NULL, les valeurs par défaut sont utilisés pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du bloc de mémoire globale contenant les données en cas de réussite ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) dans le SDK Windows.  
  
##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat  
 Appelez cette fonction à plusieurs reprises pour obtenir tous les formats disponibles pour récupérer des données à partir de l’élément.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpFormatEtc*  
 Pointe vers le [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure qui reçoit les informations de format lors de l’appel de fonction retourne.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un autre format n’est disponible ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Après un appel à [COleDataObject::BeginEnumFormats](#beginenumformats), la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données. Utilisez ces fonctions pour répertorier les formats disponibles.  
  
 Pour vérifier la disponibilité d’un format donné, appelez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) dans le SDK Windows.  
  
##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable  
 Appelez cette fonction pour déterminer si un format particulier est disponible pour récupérer des données à partir de l’élément OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cfFormat*  
 Le format de données du Presse-papiers pour être utilisé dans la structure vers laquelle pointe *lpFormatEtc*. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par le Windows native [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) (fonction).  
  
 *lpFormatEtc*  
 Pointe vers un [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) structure qui décrit le format souhaité. Indiquez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par *cfFormat*. Si sa valeur est NULL, les valeurs par défaut sont utilisés pour les autres champs dans le `FORMATETC` structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les données sont disponibles dans le format spécifié ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utile avant d’appeler `GetData`, `GetFileData`, ou `GetGlobalData`.  
  
 Pour plus d’informations, consultez [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) et [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) dans le SDK Windows.  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>  COleDataObject::Release  
 Appelez cette fonction pour libérer la possession de la [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) objet qui a été associé précédemment à le `COleDataObject` objet.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Notes  
 Le `IDataObject` a été associé à la `COleDataObject` en appelant `Attach` ou `AttachClipboard` explicitement ou par l’infrastructure. Si le *bAutoRelease* paramètre de `Attach` est FALSE, le `IDataObject` objet n’est pas libéré. Dans ce cas, l’appelant est chargé de libérer la `IDataObject` en appelant [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDataSource, classe](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem, classe](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
