---
title: COleDataObject, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: e9cb8c452cc3eea32b6eed9bf23fb454344c105d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214085"
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
|[COleDataObject :: COleDataObject](#coledataobject)|Construit un objet `COleDataObject`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDataObject :: Attach](#attach)|Attache l’objet de données OLE spécifié à `COleDataObject` .|
|[COleDataObject :: AttachClipboard](#attachclipboard)|Attache l’objet de données qui se trouve dans le presse-papiers.|
|[COleDataObject :: BeginEnumFormats](#beginenumformats)|Prépare un ou plusieurs `GetNextFormat` appels suivants.|
|[COleDataObject ::D Etach](#detach)|Détache l’objet associé `IDataObject` .|
|[COleDataObject :: GetData](#getdata)|Copie les données de l’objet de données OLE attaché dans un format spécifié.|
|[COleDataObject :: GetFileData](#getfiledata)|Copie les données de l’objet de données OLE attaché dans un `CFile` pointeur dans le format spécifié.|
|[COleDataObject :: GetGlobalData](#getglobaldata)|Copie les données de l’objet de données OLE attaché dans un `HGLOBAL` dans le format spécifié.|
|[COleDataObject :: GetNextFormat](#getnextformat)|Retourne le format de données suivant disponible.|
|[COleDataObject :: IsDataAvailable](#isdataavailable)|Vérifie si les données sont disponibles dans un format spécifié.|
|[COleDataObject :: Release](#release)|Détache et libère l’objet associé `IDataObject` .|

## <a name="remarks"></a>Notes

`COleDataObject`n’a pas de classe de base.

Ces types de transferts de données incluent une source et une destination. La source de données est implémentée en tant qu’objet de la classe [COleDataSource](../../mfc/reference/coledatasource-class.md) . Chaque fois qu’une application de destination contient des données ou qu’elle est invitée à effectuer une opération de collage à partir du presse-papiers, un objet de la `COleDataObject` classe doit être créé.

Cette classe vous permet de déterminer si les données existent dans un format spécifié. Vous pouvez également énumérer les formats de données disponibles ou vérifier si un format donné est disponible, puis récupérer les données dans le format par défaut. La récupération d’objets peut être accomplie de plusieurs façons différentes, notamment l’utilisation d’un [CFile](../../mfc/reference/cfile-class.md), d’un HGLOBAL ou d’une `STGMEDIUM` structure.

Pour plus d’informations, consultez la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans le SDK Windows.

Pour plus d’informations sur l’utilisation des objets de données dans votre application, consultez l’article [objets de données et sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleDataObject`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject :: Attach

Appelez cette fonction pour associer l' `COleDataObject` objet à un objet de données OLE.

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpDataObject*<br/>
Pointe vers un objet de données OLE.

*bAutoRelease*<br/>
TRUE si l’objet de données OLE doit être libéré lorsque l' `COleDataObject` objet est détruit ; sinon, false.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) dans le SDK Windows.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject :: AttachClipboard

Appelez cette fonction pour attacher l’objet de données qui se trouve actuellement dans le presse-papiers à l' `COleDataObject` objet.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

> [!NOTE]
> L’appel de cette fonction verrouille le presse-papiers jusqu’à ce que cet objet de données soit libéré. L’objet de données est libéré dans le destructeur de `COleDataObject` . Pour plus d’informations, consultez [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) et [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) dans la documentation Win32.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject :: BeginEnumFormats

Appelez cette fonction pour préparer les appels suivants à `GetNextFormat` pour la récupération d’une liste de formats de données à partir de l’élément.

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>Notes

Après un appel à `BeginEnumFormats` , la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumèrent la liste des formats disponibles dans l’objet de données.

Pour vérifier la disponibilité des données dans un format donné, utilisez [COleDataObject :: IsDataAvailable](#isdataavailable).

Pour plus d’informations, consultez [IDataObject :: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) dans la SDK Windows.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject :: COleDataObject

Construit un objet `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Notes

Un appel à [COleDataObject :: Attach](#attach) ou [COleDataObject :: AttachClipboard](#attachclipboard) doit être effectué avant d’appeler d’autres `COleDataObject` fonctions.

> [!NOTE]
> Étant donné que l’un des paramètres des gestionnaires de glisser-déplacer est un pointeur vers un `COleDataObject` , il n’est pas nécessaire d’appeler ce constructeur pour prendre en charge le glisser-déplacer.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject ::D Etach

Appelez cette fonction pour détacher l’objet `COleDataObject` de l’objet de données OLE associé sans libérer l’objet de données.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet de données OLE détaché.

### <a name="remarks"></a>Notes

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject :: GetData

Appelez cette fonction pour récupérer des données de l’élément dans le format spécifié.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpStgMedium*<br/>
Pointe vers une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) qui recevra des données.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [IDataObject :: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject :: GetFileData

Appelez cette fonction pour créer un `CFile` `CFile` objet dérivé de ou et récupérer des données dans le format spécifié dans un `CFile` pointeur.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le nouvel `CFile` `CFile` objet ou dérivé contenant les données en cas de réussite ; sinon, null.

### <a name="remarks"></a>Notes

Selon le support dans lequel les données sont stockées, le type réel vers lequel pointe la valeur de retour peut être `CFile` , `CSharedFile` ou `COleStreamFile` .

> [!NOTE]
> L' `CFile` objet auquel accède la valeur de retour de cette fonction est détenu par l’appelant. C’est la responsabilité de l’appelant de **`delete`** l' `CFile` objet, ce qui a pour effet de fermer le fichier.

Pour plus d’informations, consultez [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject :: GetGlobalData

Appelez cette fonction pour allouer un bloc de mémoire globale et récupérer des données dans le format spécifié dans un HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournissez une valeur pour ce paramètre si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="return-value"></a>Valeur de retour

Handle du bloc de mémoire globale contenant les données en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject :: GetNextFormat

Appelez cette fonction à plusieurs reprises pour obtenir tous les formats disponibles pour la récupération de données à partir de l’élément.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Pointe vers la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) qui reçoit les informations de mise en forme lors du retour de l’appel de fonction.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si un autre format est disponible ; Sinon, 0.

### <a name="remarks"></a>Notes

Après un appel à [COleDataObject :: BeginEnumFormats](#beginenumformats), la position du premier format pris en charge par cet objet de données est stockée. Les appels successifs à `GetNextFormat` énumèrent la liste des formats disponibles dans l’objet de données. Utilisez ces fonctions pour répertorier les formats disponibles.

Pour vérifier la disponibilité d’un format donné, appelez [COleDataObject :: IsDataAvailable](#isdataavailable).

Pour plus d’informations, consultez [IEnumXXXX :: Next](/previous-versions/ms695273\(v=vs.85\)) dans le SDK Windows.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject :: IsDataAvailable

Appelez cette fonction pour déterminer si un format particulier est disponible pour la récupération de données à partir de l’élément OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Format de données du presse-papiers à utiliser dans la structure vers laquelle pointe *lpFormatEtc*. Ce paramètre peut être l’un des formats de presse-papiers prédéfinis ou la valeur retournée par la fonction Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) native.

*lpFormatEtc*<br/>
Pointe vers une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format souhaité. Fournissez une valeur pour ce paramètre uniquement si vous souhaitez spécifier des informations de mise en forme supplémentaires au-delà du format du presse-papiers spécifié par *cfFormat*. Si la valeur est NULL, les valeurs par défaut sont utilisées pour les autres champs de la `FORMATETC` structure.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les données sont disponibles dans le format spécifié ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est utile avant d’appeler `GetData` , `GetFileData` ou `GetGlobalData` .

Pour plus d’informations, consultez [IDataObject :: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, consultez [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject :: Release

Appelez cette fonction pour libérer la propriété de l’objet [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) précédemment associé à l' `COleDataObject` objet.

```cpp
void Release();
```

### <a name="remarks"></a>Notes

Le `IDataObject` a été associé au `COleDataObject` en appelant `Attach` ou `AttachClipboard` explicitement ou par l’infrastructure. Si le paramètre *bAutoRelease* de `Attach` a la valeur false, l’objet n’est `IDataObject` pas libéré. Dans ce cas, l’appelant est responsable de la libération de `IDataObject` en appelant [IUnknown :: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource, classe](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
