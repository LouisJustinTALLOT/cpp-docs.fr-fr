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
ms.openlocfilehash: 8b9565382de8ae731c166f60a0d1994c1b948a7b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753912"
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
|[COleDataObject::Attach](#attach)|Attache l’objet de données `COleDataObject`OLE spécifiée à la .|
|[COleDataObject::AttachClipboard](#attachclipboard)|Attache l’objet de données qui se trouve sur le Clipboard.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Se prépare pour un `GetNextFormat` ou plusieurs appels ultérieurs.|
|[COleDataObject::Detach](#detach)|Détache l’objet `IDataObject` associé.|
|[COleDataObject::GetData](#getdata)|Copiez les données de l’objet de données OLE ci-joint dans un format spécifié.|
|[COleDataObject::GetFileData](#getfiledata)|Copie les données de l’objet `CFile` de données OLE ci-joint dans un pointeur dans le format spécifié.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Copie les données de l’objet `HGLOBAL` de données OLE ci-joint dans un format spécifié.|
|[COleDataObject::GetNextFormat](#getnextformat)|Retourne le format de données suivant disponible.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Vérifie si les données sont disponibles dans un format spécifié.|
|[COleDataObject::Libération](#release)|Détache et libère l’objet associé. `IDataObject`|

## <a name="remarks"></a>Notes

`COleDataObject`n’a pas de classe de base.

Ces types de transferts de données comprennent une source et une destination. La source de données est implémentée comme objet de la classe [COleDataSource.](../../mfc/reference/coledatasource-class.md) Chaque fois qu’une application de destination a des données supprimées ou est demandée d’effectuer une opération de pâte à partir du Clipboard, un objet de la `COleDataObject` classe doit être créé.

Cette classe vous permet de déterminer si les données existent dans un format spécifié. Vous pouvez également énumérer les formats de données disponibles ou vérifier si un format donné est disponible, puis récupérer les données dans le format préféré. La récupération d’objets peut être effectuée de plusieurs façons différentes, y compris l’utilisation d’un [CFile](../../mfc/reference/cfile-class.md), d’un HGLOBAL ou d’une `STGMEDIUM` structure.

Pour plus d’informations, voir la structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) dans le SDK Windows.

Pour plus d’informations sur l’utilisation d’objets de données dans votre application, consultez l’article [Data Objects and Data Sources (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleDataObject`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject::Attach

Appelez cette fonction `COleDataObject` pour associer l’objet à un objet de données OLE.

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpDataObject*<br/>
Indique un objet de données OLE.

*bAutoRelease*<br/>
VRAI si l’objet de données `COleDataObject` OLE doit être libéré lorsque l’objet est détruit; autrement FALSE.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) dans le SDK Windows.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard

Appelez cette fonction pour attacher l’objet de données `COleDataObject` qui se trouve actuellement sur le Clipboard à l’objet.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

> [!NOTE]
> L’appel de cette fonction verrouille le Clipboard jusqu’à ce que cet objet de données soit libéré. L’objet de données est libéré `COleDataObject`dans le destructor pour le . Pour plus d’informations, voir [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) et [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) dans la documention Win32.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Appelez cette fonction pour vous `GetNextFormat` préparer aux appels ultérieurs pour récupérer une liste de formats de données à partir de l’élément.

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>Notes

Après un `BeginEnumFormats`appel à , la position du premier format pris en charge par cet objet de données est stockée. Les appels `GetNextFormat` successifs pour énumérer la liste des formats disponibles dans l’objet de données.

Pour vérifier la disponibilité des données dans un format donné, utilisez [COleDataObject::IsDataAvailable](#isdataavailable).

Pour plus d’informations, voir [IDataObject:EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) dans le Windows SDK.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject

Construit un objet `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Notes

Un appel à [COleDataObject::Attach](#attach) ou [COleDataObject::AttachClipboard](#attachclipboard) `COleDataObject` doit être fait avant d’appeler d’autres fonctions.

> [!NOTE]
> Puisque l’un des paramètres pour les gestionnaires de drag-and-drop est un pointeur à un `COleDataObject`, il n’est pas nécessaire d’appeler ce constructeur pour soutenir la traînée et la baisse.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach

Appelez cette fonction pour `COleDataObject` détacher l’objet de son objet de données OLE associé sans libérer l’objet de données.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de l’objet de données OLE qui a été détaché.

### <a name="remarks"></a>Notes

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData

Appelez cette fonction pour récupérer les données de l’élément dans le format spécifié.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgMedium*<br/>
Indique une structure [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) qui recevra des données.

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les valeurs `FORMATETC` par défaut sont utilisées pour les autres champs de la structure.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [IDataObject:GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1), et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData

Appelez cette fonction `CFile` pour `CFile`créer un objet ou dérivé et `CFile` pour récupérer des données dans le format spécifié dans un pointeur.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les valeurs `FORMATETC` par défaut sont utilisées pour les autres champs de la structure.

### <a name="return-value"></a>Valeur de retour

Pointer vers `CFile` l’objet nouveau ou `CFile`dérivé contenant les données en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Selon le support dans lequel les données sont stockées, le `CFile` `CSharedFile`type `COleStreamFile`réel indiqué par la valeur de rendement peut être, ou .

> [!NOTE]
> L’objet `CFile` accessible par la valeur de retour de cette fonction appartient à l’appelant. Il incombe à l’appelant `CFile` de **supprimer** l’objet, fermant ainsi le fichier.

Pour plus d’informations, voir [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans windows SDK.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData

Appelez cette fonction pour allouer un bloc de mémoire global et pour récupérer des données dans le format spécifié dans un HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format dans lequel les données doivent être retournées. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format dans lequel les données doivent être retournées. Fournir une valeur pour ce paramètre si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les valeurs `FORMATETC` par défaut sont utilisées pour les autres champs de la structure.

### <a name="return-value"></a>Valeur de retour

La poignée du bloc mémoire global contenant les données en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans windows SDK.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat

Appelez cette fonction à plusieurs reprises pour obtenir tous les formats disponibles pour récupérer les données de l’élément.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Paramètres

*lpFormatEtc*<br/>
Indique la structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) qui reçoit les informations de format lorsque l’appel de fonction revient.

### <a name="return-value"></a>Valeur de retour

Nonzero si un autre format est disponible; sinon 0.

### <a name="remarks"></a>Notes

Après un appel à [COleDataObject::BeginEnumFormats](#beginenumformats), la position du premier format pris en charge par cet objet de données est stockée. Les appels `GetNextFormat` successifs pour énumérer la liste des formats disponibles dans l’objet de données. Utilisez ces fonctions pour énumérer les formats disponibles.

Pour vérifier la disponibilité d’un format donné, appelez [COleDataObject::IsDataAvailable](#isdataavailable).

Pour plus d’informations, voir [IEnumXXXX::Next](/previous-versions/ms695273\(v=vs.85\)) in the Windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::IsDataAvailable

Appelez cette fonction pour déterminer si un format particulier est disponible pour récupérer les données de l’élément OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Paramètres

*cfFormat*<br/>
Le format de données Clipboard à utiliser dans la structure indiquée par *lpFormatEtc*. Ce paramètre peut être l’un des formats Predefined Clipboard ou la valeur retournée par la fonction native Windows [RegisterClipboardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Indique une structure [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) décrivant le format souhaité. Fournir une valeur pour ce paramètre que si vous souhaitez spécifier des informations de format supplémentaires au-delà du format Clipboard spécifié par *cfFormat*. S’il s’agit de NULL, les valeurs `FORMATETC` par défaut sont utilisées pour les autres champs de la structure.

### <a name="return-value"></a>Valeur de retour

Nonzero si les données sont disponibles dans le format spécifié; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est `GetData`utile `GetFileData`avant `GetGlobalData`d’appeler , , ou .

Pour plus d’informations, voir [IDataObject:QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) et [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) dans le SDK Windows.

Pour plus d’informations, voir [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) dans le Windows SDK.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView:QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject::Libération

Appelez cette fonction pour libérer la propriété de l’objet `COleDataObject` [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) qui était auparavant associé à l’objet.

```cpp
void Release();
```

### <a name="remarks"></a>Notes

Le `IDataObject` a été `COleDataObject` associé `Attach` `AttachClipboard` à l’appel ou explicitement ou par le cadre. Si le *paramètre bAutoRelease* `Attach` `IDataObject` est FALSE, l’objet ne sera pas libéré. Dans ce cas, l’appelant est `IDataObject` responsable de la libération de l’en appelant [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource, classe](../../mfc/reference/coledatasource-class.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
