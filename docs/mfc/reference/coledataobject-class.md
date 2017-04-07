---
title: Classe de COleDataObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject interface, MFC encapsulation
- data transfer [C++]
- data transfer [C++], OLE
- OLE data transfer [C++]
- COleDataObject class
- uniform data transfer, OLE
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f30ca208252fe81f1e47d9e8f817cb9137656540
ms.lasthandoff: 02/24/2017

---
# <a name="coledataobject-class"></a>COleDataObject (classe)
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
|[COleDataObject::AttachClipboard](#attachclipboard)|Attache l’objet de données dans le Presse-papiers.|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Prépare pour un ou plus ultérieures `GetNextFormat` appels.|  
|[COleDataObject::Detach](#detach)|Détache associé `IDataObject` objet.|  
|[COleDataObject::GetData](#getdata)|Copie des données à partir de l’objet de données OLE attaché dans un format spécifié.|  
|[COleDataObject::GetFileData](#getfiledata)|Copie les données de l’objet de données OLE joint dans un `CFile` pointeur au format spécifié.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Copie les données de l’objet de données OLE joint dans un `HGLOBAL` au format spécifié.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Renvoie le format de données suivant disponible.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Vérifie si les données sont disponibles dans un format spécifié.|  
|[COleDataObject::Release](#release)|Détache et libère associé `IDataObject` objet.|  
  
## <a name="remarks"></a>Remarques  
 `COleDataObject`n’a pas d’une classe de base.  
  
 Ces types de transferts de données incluent une source et une destination. La source de données est implémentée en tant qu’objet de la [COleDataSource](../../mfc/reference/coledatasource-class.md) classe. Chaque fois qu’une application de destination a supprimé qu’il contient des données ou est invitée à effectuer une opération de collage depuis le Presse-papiers, un objet de la `COleDataObject` classe doit être créée.  
  
 Cette classe vous permet de déterminer si les données existent dans un format spécifié. Vous pouvez également énumérer les formats de données disponibles ou vérifier si un format donné est disponible et récupérer les données dans le format par défaut. La récupération d’objets est possible de différentes façons, notamment l’utilisation d’un [CFile](../../mfc/reference/cfile-class.md), un `HGLOBAL`, ou une **STGMEDIUM** structure.  
  
 Pour plus d’informations, consultez la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) de la structure dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations sur l’utilisation des objets de données dans votre application, consultez l’article [des objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `COleDataObject`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="attach"></a>COleDataObject::Attach  
 Appelez cette fonction pour associer le `COleDataObject` objet avec un objet de données OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *objet lpDataObject*  
 Pointe vers un objet de données OLE.  
  
 `bAutoRelease`  
 **TRUE** si l’objet de données OLE doit être libérée lorsque la `COleDataObject` objet est détruite ; sinon **FALSE**.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 Appelez cette fonction pour attacher l’objet de données qui est actuellement dans le Presse-papiers pour le `COleDataObject` objet.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Appeler cette fonction de verrouillage du Presse-papiers jusqu'à ce que cet objet de données. L’objet de données est libéré dans le destructeur de la `COleDataObject`. Pour plus d’informations, consultez [ouverture du Presse-papiers](http://msdn.microsoft.com/library/windows/desktop/ms649048) et [la fermeture du Presse-papiers](http://msdn.microsoft.com/library/windows/desktop/ms649035) dans la documentation de Win32.  
  
##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats  
 Appelez cette fonction pour préparer les appels ultérieurs à `GetNextFormat` pour récupérer une liste de formats de données à partir de l’élément.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Notes  
 Après un appel à `BeginEnumFormats`, la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données.  
  
 Pour vérifier la disponibilité des données dans un format donné, utilisez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="coledataobject"></a>COleDataObject::COleDataObject  
 Construit un objet `COleDataObject`.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Notes  
 Un appel à [COleDataObject::Attach](#attach) ou [COleDataObject::AttachClipboard](#attachclipboard) doivent être effectuées avant d’appeler d’autres `COleDataObject` fonctions.  
  
> [!NOTE]
>  Étant donné qu’un des paramètres pour les gestionnaires de glisser-déplacer est un pointeur vers un `COleDataObject`, il n’est pas nécessaire d’appeler ce constructeur pour prendre en charge le glisser -déplacer.  
  
##  <a name="detach"></a>COleDataObject::Detach  
 Appelez cette fonction pour détacher le `COleDataObject` objet à partir de l’objet de données associé OLE sans libérer l’objet de données.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet de données OLE qui a été détachée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdata"></a>COleDataObject::GetData  
 Appelez cette fonction pour récupérer des données à partir de l’élément dans le format spécifié.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `cfFormat`  
 Le format dans lequel les données doit être retournée. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par Windows native [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 `lpStgMedium`  
 Pointe vers une [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) structure qui recevra les données.  
  
 `lpFormatEtc`  
 Pointe vers une [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure décrivant le format dans lequel les données doit être retournée. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par `cfFormat`. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getfiledata"></a>COleDataObject::GetFileData  
 Appelez cette fonction pour créer un `CFile` ou `CFile`-objet dérivé et récupérer les données au format spécifié dans un `CFile` pointeur.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `cfFormat`  
 Le format dans lequel les données doit être retournée. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par Windows native [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 `lpFormatEtc`  
 Pointe vers une [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure décrivant le format dans lequel les données doit être retournée. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par `cfFormat`. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la nouvelle `CFile` ou `CFile`-objet dérivé contenant les données de cas de réussite ; sinon **NULL**.  
  
### <a name="remarks"></a>Notes  
 Selon le support, les données sont stockées dans, le type réel désigné par la valeur de retour peut être `CFile`, `CSharedFile`, ou `COleStreamFile`.  
  
> [!NOTE]
>  Le `CFile` objet accédé par la valeur de retour de cette fonction est possédée par l’appelant. Il incombe à l’appelant de **supprimer** le `CFile` objet, donc fermer le fichier.  
  
 Pour plus d’informations, consultez [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 Appelez cette fonction pour allouer un bloc de mémoire globale et pour récupérer des données au format spécifié dans un `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `cfFormat`  
 Le format dans lequel les données doit être retournée. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par Windows native [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 `lpFormatEtc`  
 Pointe vers une [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure décrivant le format dans lequel les données doit être retournée. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par `cfFormat`. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du bloc de mémoire globale contenant les données en cas de réussite ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getnextformat"></a>COleDataObject::GetNextFormat  
 Appelez cette fonction à plusieurs reprises pour obtenir tous les formats disponibles pour la récupération de données à partir de l’élément.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpFormatEtc`  
 Pointe vers le [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure qui reçoit les informations de format lors de l’appel de fonction retourne.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un autre format est disponible ; sinon 0.  
  
### <a name="remarks"></a>Remarques  
 Après un appel à [COleDataObject::BeginEnumFormats](#beginenumformats), la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumère la liste des formats disponibles dans l’objet de données. Utilisez ces fonctions pour répertorier les formats disponibles.  
  
 Pour vérifier la disponibilité d’un format donné, appelez [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Pour plus d’informations, consultez [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="isdataavailable"></a>COleDataObject::IsDataAvailable  
 Appelez cette fonction pour déterminer si un format particulier est disponible pour la récupération de données à partir de l’élément OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `cfFormat`  
 Le format de données de Presse-papiers pour être utilisé dans la structure vers laquelle pointe `lpFormatEtc`. Ce paramètre peut être un des formats de Presse-papiers prédéfinis ou la valeur retournée par Windows native [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) (fonction).  
  
 `lpFormatEtc`  
 Pointe vers une [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure décrivant le format désiré. Fournir une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de format supplémentaires au-delà du format de Presse-papiers spécifié par `cfFormat`. S’il s’agit **NULL**, les valeurs par défaut sont utilisées pour les autres champs de la **FORMATETC** structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les données sont disponibles dans le format spécifié ; sinon 0.  
  
### <a name="remarks"></a>Remarques  
 Cette fonction est utile avant d’appeler `GetData`, `GetFileData`, ou `GetGlobalData`.  
  
 Pour plus d’informations, consultez [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) et [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Pour plus d’informations, consultez [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>COleDataObject::Release  
 Appelez cette fonction pour libérer la possession de la [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objet qui a été associé précédemment à le `COleDataObject` objet.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Notes  
 Le `IDataObject` a été associé à la `COleDataObject` en appelant **Attach** ou `AttachClipboard` ou explicitement par l’infrastructure. Si le `bAutoRelease` paramètre de **Attach** est **FALSE**, le `IDataObject` objet n’est pas libéré. Dans ce cas, l’appelant est responsable de la libération du `IDataObject` en appelant [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [COleDataSource (classe)](../../mfc/reference/coledatasource-class.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Classe COleServerItem](../../mfc/reference/coleserveritem-class.md)

