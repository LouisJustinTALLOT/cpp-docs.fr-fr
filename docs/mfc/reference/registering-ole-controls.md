---
title: Inscription des contrôles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2f2d7872e8b9369b5eef283e5b52a54c29afd563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372974"
---
# <a name="registering-ole-controls"></a>Inscription des contrôles OLE

Les commandes OLE, comme d’autres objets serveur OLE, peuvent être consultées par d’autres applications OLE-aware. Ceci est réalisé en enregistrant la bibliothèque et la classe de type de contrôle.

Les fonctions suivantes vous permettent d’ajouter et de supprimer la classe du contrôle, les pages de propriété et la bibliothèque de type dans la base de données d’enregistrement Windows :

### <a name="registering-ole-controls"></a>Inscription des contrôles OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Ajoute la classe du contrôle à la base de données d’enregistrement.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Ajoute une page de propriété de contrôle à la base de données d’enregistrement.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Ajoute la bibliothèque de type de contrôle à la base de données d’enregistrement.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Supprime une classe de contrôle ou une classe de page de propriété de la base de données d’enregistrement.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Supprime la bibliothèque de type du contrôle de la base de données d’enregistrement.|

`AfxOleRegisterTypeLib`est généralement appelé dans un contrôle `DllRegisterServer`DLL mise en œuvre de . De `AfxOleUnregisterTypeLib` même, `DllUnregisterServer`est appelé par . `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`et `AfxOleUnregisterClass` sont généralement `UpdateRegistry` appelés par la fonction membre de l’usine de classe d’un contrôle ou page de propriété.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass

Enregistre la classe de contrôle avec la base de données d’enregistrement Windows.

```
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,
    REFCLSID clsid,
    LPCTSTR pszProgID,
    UINT idTypeName,
    UINT idBitmap,
    int nRegFlags,
    DWORD dwMiscStatus,
    REFGUID tlid,
    WORD wVerMajor,
    WORD wVerMinor);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
La poignée d’instance du module associé à la classe de contrôle.

*clsid*<br/>
L’ID de classe unique du contrôle.

*pszProgID*<br/>
L’ID unique du programme du contrôle.

*idTypeName (idTypeName)*<br/>
L’ID de ressource de la chaîne qui contient un nom de type lisible par l’utilisateur pour le contrôle.

*idBitmap (en)*<br/>
L’ID de ressource de la bitmap utilisé pour représenter le contrôle OLE dans une barre d’outils ou une palette.

*nRegFlags*<br/>
Contient un ou plusieurs des drapeaux suivants :

- `afxRegInsertable`Permet au contrôle d’apparaître dans la boîte de dialogue Insert Object pour les objets OLE.

- `afxRegApartmentThreading`Définit le modèle de threading dans le registre à ThreadingModel-Apartment.

- `afxRegFreeThreading`Définit le modèle de threading dans le registre à ThreadingModel-Free.

   Vous pouvez combiner `afxRegApartmentThreading` les `afxRegFreeThreading` deux drapeaux et définir ThreadingModel-Both. Voir [InprocServer32](/windows/win32/com/inprocserver32) dans le Windows SDK pour plus d’informations sur l’enregistrement des modèles de threading.

> [!NOTE]
> Dans les versions MFC avant MFC 4.2, le **paramètre int** *nRegFlags* était un paramètre BOOL, *bInsertable*, qui a permis ou refusé le contrôle d’être inséré à partir de la boîte de dialogue Insert Object.

*dwMiscStatus*<br/>
Contient un ou plusieurs des drapeaux de statut suivants (pour une description des drapeaux, voir recensement OLEMISC dans le SDK Windows):

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid tlid*<br/>
L’ID unique de la classe de contrôle.

*wVerMajor (en)*<br/>
Le numéro de version principal de la classe de contrôle.

*wVerMinor (en)*<br/>
Le numéro de version mineur de la classe de contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si la classe de contrôle a été enregistrée; sinon 0.

### <a name="remarks"></a>Notes

Cela permet d’utiliser le contrôle par les conteneurs qui sont OLE-contrôle conscient. `AfxOleRegisterControlClass`met à jour le registre avec le nom et l’emplacement du contrôle sur le système et définit également le modèle de threading que le contrôle prend en charge dans le registre. Pour plus d’informations, voir [Note technique 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Appartement-Modèle Threading in OLE Controls," et [About Processes and Threads](/windows/win32/ProcThread/about-processes-and-threads) in the Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

L’exemple ci-dessus montre comment `AfxOleRegisterControlClass` est appelé avec le drapeau pour inséré et le drapeau pour le modèle d’appartement ORed ensemble pour créer le sixième paramètre:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Le contrôle apparaîtra dans la boîte de dialogue Insert Object pour les conteneurs activés, et il sera appartement modèle-conscient. Les contrôles de type d’appartement doivent s’assurer que les données statiques de classe sont protégées par des serrures, de sorte que tandis qu’un contrôle dans un appartement accède aux données statiques, il n’est pas désactivé par le planificateur avant qu’il soit terminé, et un autre cas de la même classe commence à utiliser les mêmes données statiques. Tous les accès aux données statiques seront entourés de code de section critique.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass

Enregistre la classe de page de propriété avec la base de données d’enregistrement Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
La poignée d’instance du module associé à la classe de page de propriété.

*clsid*<br/>
L’ID de classe unique de la page de propriété.

*idTypeName (idTypeName)*<br/>
L’ID de ressource de la chaîne qui contient un nom lisible à l’utilisateur pour la page de propriété.

*nRegFlags*<br/>
Peut contenir le drapeau:

- `afxRegApartmentThreading`Définit le modèle de threading dans le registre à ThreadingModel appartement.

> [!NOTE]
> Dans les versions MFC avant MFC 4.2, le **paramètre int** *nRegFlags* n’était pas disponible. Notez également `afxRegInsertable` que le drapeau n’est pas une option valide pour les pages de propriété et provoquera un ASSERT dans MFC s’il est réglé

### <a name="return-value"></a>Valeur de retour

Nonzero si la classe de contrôle a été enregistrée; sinon 0.

### <a name="remarks"></a>Notes

Cela permet à la page de propriété d’être utilisée par des conteneurs qui sont OLE-contrôle conscient. `AfxOleRegisterPropertyPageClass`met à jour le registre avec le nom de la page de propriété et son emplacement sur le système et définit également le modèle de threading que le contrôle prend en charge dans le registre. Pour plus d’informations, voir [Note technique 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "Appartement-Modèle Threading in OLE Controls," et [About Processes and Threads](/windows/win32/ProcThread/about-processes-and-threads) in the Windows SDK.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib

Enregistre la bibliothèque type avec la base de données d’enregistrement Windows et permet à la bibliothèque type d’être utilisé par d’autres conteneurs qui sont OLE-contrôle conscient.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
La poignée d’instance de l’application associée à la bibliothèque de type.

*tlid tlid*<br/>
L’ID unique de la bibliothèque de type.

*pszFileName*<br/>
Indique le nom de fichier optionnel d’une bibliothèque de type localisé (. TLB) fichier pour le contrôle.

*pszHelpDir*<br/>
Le nom de l’annuaire où le fichier d’aide pour la bibliothèque de type peut être trouvé. Si NULL, le fichier d’aide est supposé être dans le même répertoire que la bibliothèque de type elle-même.

### <a name="return-value"></a>Valeur de retour

Nonzero si la bibliothèque de type a été enregistrée; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction met à jour le registre avec le nom de la bibliothèque de type et son emplacement sur le système.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass

Supprime l’entrée de classe de la page de contrôle ou de propriété de la base de données d’enregistrement Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Paramètres

*Clsid*<br/>
L’ID de classe unique de la page de contrôle ou de propriété.

*pszProgID*<br/>
L’ID unique du programme de la page de contrôle ou de propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si la classe de la page de contrôle ou de propriété n’était pas enregistrée avec succès; sinon 0.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregregisterTypeLib

Appelez cette fonction pour supprimer l’entrée de bibliothèque de type de la base de données d’enregistrement Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Paramètres

*tlID (en anglais)*<br/>
L’ID unique de la bibliothèque de type.

### <a name="return-value"></a>Valeur de retour

Nonzero si la bibliothèque de type n’était pas enregistrée avec succès; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
