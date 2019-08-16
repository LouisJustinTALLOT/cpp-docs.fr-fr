---
title: Inscription des contrôles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9fcbc002913cc6cce86276796a371231ef0f32e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501991"
---
# <a name="registering-ole-controls"></a>Inscription des contrôles OLE

Les contrôles OLE, comme d’autres objets serveur OLE, sont accessibles par d’autres applications prenant en charge OLE. Pour ce faire, vous devez inscrire la classe et la bibliothèque de types du contrôle.

Les fonctions suivantes vous permettent d’ajouter et de supprimer la classe, les pages de propriétés et la bibliothèque de types du contrôle dans la base de données d’inscription Windows:

### <a name="registering-ole-controls"></a>Inscription des contrôles OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Ajoute la classe du contrôle à la base de données d’inscription.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Ajoute une page de propriétés de contrôle à la base de données d’inscription.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Ajoute la bibliothèque de types du contrôle à la base de données d’inscription.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Supprime une classe de contrôle ou une classe de page de propriétés de la base de données d’inscription.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Supprime la bibliothèque de types du contrôle de la base de données d’inscription.|

`AfxOleRegisterTypeLib`est généralement appelé dans l’implémentation d’une DLL de `DllRegisterServer`contrôle de. De même, `AfxOleUnregisterTypeLib` est appelé par `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, et `AfxOleUnregisterClass` sont généralement appelés par la `UpdateRegistry` fonction membre de la fabrique de classes ou de la page de propriétés d’un contrôle.

##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass

Inscrit la classe de contrôle avec la base de données d’inscription Windows.

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
Handle d’instance du module associé à la classe de contrôle.

*clsid*<br/>
ID de classe unique du contrôle.

*pszProgID*<br/>
ID de programme unique du contrôle.

*idTypeName*<br/>
ID de ressource de la chaîne qui contient un nom de type lisible par l’utilisateur pour le contrôle.

*idBitmap*<br/>
ID de ressource de la bitmap utilisée pour représenter le contrôle OLE dans une barre d’outils ou une palette.

*nRegFlags*<br/>
Contient un ou plusieurs des indicateurs suivants:

- `afxRegInsertable`Permet d’afficher le contrôle dans la boîte de dialogue Insérer un objet pour les objets OLE.

- `afxRegApartmentThreading`Définit le modèle de thread dans le registre sur ThreadingModel = Apartment.

- `afxRegFreeThreading`Définit le modèle de thread dans le registre sur ThreadingModel = Free.

   Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` définir ThreadingModel = les deux. Pour plus d’informations sur l’inscription du modèle de thread, consultez [InprocServer32](/windows/win32/com/inprocserver32) dans le SDK Windows.

> [!NOTE]
>  Dans les versions MFC antérieures à MFC 4,2, le paramètre **int** *nRegFlags* était un paramètre bool, *bInsertable*, qui permettait d’insérer ou non le contrôle à partir de la boîte de dialogue Insérer un objet.

*dwMiscStatus*<br/>
Contient un ou plusieurs des indicateurs d’état suivants (pour obtenir une description des indicateurs, consultez OLEMISC, énumération dans le SDK Windows):

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

*tlid*<br/>
ID unique de la classe de contrôle.

*wVerMajor*<br/>
Numéro de version principale de la classe de contrôle.

*wVerMinor*<br/>
Numéro de version mineure de la classe de contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de contrôle a été inscrite; Sinon, 0.

### <a name="remarks"></a>Notes

Cela permet au contrôle d’être utilisé par des conteneurs qui prennent en charge le contrôle OLE. `AfxOleRegisterControlClass`met à jour le Registre avec le nom et l’emplacement du contrôle sur le système et définit également le modèle de thread que le contrôle prend en charge dans le registre. Pour plus d’informations, consultez la [note technique 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), «cloisonnement-Model Threading in OLE Controls», et [à propos des processus et](/windows/win32/ProcThread/about-processes-and-threads) des threads dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

L’exemple ci-dessus `AfxOleRegisterControlClass` montre comment est appelé avec l’indicateur pour l’insertion et l’indicateur pour le modèle Apartment avec l’opérateur or pour créer le sixième paramètre:

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Le contrôle s’affiche dans la boîte de dialogue Insérer un objet pour les conteneurs activés et prend en charge le modèle de cloisonnement. Les contrôles de type Apartment doivent s’assurer que les données de classe statiques sont protégées par des verrous, de sorte que si un contrôle dans un cloisonnement accède aux données statiques, il n’est pas désactivé par le planificateur avant qu’il ne soit terminé, et une autre instance de la même classe commence à utiliser mêmes données statiques. Tous les accès aux données statiques sont entourés d’un code de section critique.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl. h

##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass

Inscrit la classe de page de propriétés avec la base de données d’inscription Windows.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Handle d’instance du module associé à la classe de la page de propriétés.

*clsid*<br/>
ID de classe unique de la page de propriétés.

*idTypeName*<br/>
ID de ressource de la chaîne qui contient un nom lisible par l’utilisateur pour la page de propriétés.

*nRegFlags*<br/>
Peut contenir l’indicateur:

- `afxRegApartmentThreading`Définit le modèle de thread dans le registre sur ThreadingModel = Apartment.

> [!NOTE]
>  Dans les versions MFC antérieures à MFC 4,2, le paramètre **int** *nRegFlags* n’était pas disponible. Notez également que l' `afxRegInsertable` indicateur n’est pas une option valide pour les pages de propriétés et déclenchera une assertion dans MFC si elle est définie

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de contrôle a été inscrite; Sinon, 0.

### <a name="remarks"></a>Notes

Cela permet à la page de propriétés d’être utilisée par les conteneurs qui prennent en charge le contrôle OLE. `AfxOleRegisterPropertyPageClass`met à jour le Registre avec le nom de la page de propriétés et son emplacement sur le système, et définit également le modèle de thread que le contrôle prend en charge dans le registre. Pour plus d’informations, consultez la [note technique 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), «cloisonnement-Model Threading in OLE Controls», et [à propos des processus et](/windows/win32/ProcThread/about-processes-and-threads) des threads dans le SDK Windows.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl. h

##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib

Inscrit la bibliothèque de types avec la base de données d’inscription Windows et permet à la bibliothèque de types d’être utilisée par d’autres conteneurs qui prennent en charge le contrôle OLE.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Handle d’instance de l’application associée à la bibliothèque de types.

*tlid*<br/>
ID unique de la bibliothèque de types.

*pszFileName*<br/>
Pointe vers le nom de fichier facultatif d’une bibliothèque de types localisée (. TLB) pour le contrôle.

*pszHelpDir*<br/>
Nom du répertoire dans lequel se trouve le fichier d’aide de la bibliothèque de types. Si la valeur est NULL, le fichier d’aide est supposé être dans le même répertoire que la bibliothèque de types elle-même.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la bibliothèque de types a été inscrite; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction met à jour le Registre avec le nom de la bibliothèque de types et son emplacement sur le système.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

Supprime l’entrée de classe de contrôle ou de page de propriétés de la base de données d’inscription Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Paramètres

*clsID*<br/>
ID de classe unique de la page de propriétés ou de contrôle.

*pszProgID*<br/>
ID de programme unique de la page de propriétés ou de contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’inscription de la classe de contrôle ou de page de propriétés a été correctement annulée; Sinon, 0.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl. h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

Appelez cette fonction pour supprimer l’entrée de la bibliothèque de types de la base de données d’inscription Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Paramètres

*tlID*<br/>
ID unique de la bibliothèque de types.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’inscription de la bibliothèque de types a été correctement annulée; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
