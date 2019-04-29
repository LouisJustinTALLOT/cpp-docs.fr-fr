---
title: Inscription des contrôles OLE
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.ole
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 9c480696bdec3591f0509cbad04051a2b3af4070
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310134"
---
# <a name="registering-ole-controls"></a>Inscription des contrôles OLE

Contrôles OLE, comme les autres objets de serveur OLE, sont accessibles par d’autres applications prenant en charge OLE. Pour cela, vous devez inscrire la bibliothèque de types et la classe du contrôle.

Les fonctions suivantes permettent d’ajouter et supprimer la classe du contrôle, de pages de propriétés et de bibliothèque de types dans la base de données d’inscription Windows :

### <a name="registering-ole-controls"></a>Inscription des contrôles OLE

|||
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|Ajoute la classe du contrôle à la base de données d’inscription.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|Ajoute une page de propriétés de contrôle à la base de données d’inscription.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|Ajoute la bibliothèque de types du contrôle à la base de données d’inscription.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|Supprime une classe de contrôle ou une classe de page de propriétés de la base de données d’inscription.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|Supprime la bibliothèque de types du contrôle à partir de la base de données d’inscription.|

`AfxOleRegisterTypeLib` est généralement appelée dans l’implémentation d’une DLL de contrôle de `DllRegisterServer`. De même, `AfxOleUnregisterTypeLib` est appelée par `DllUnregisterServer`. `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass`, et `AfxOleUnregisterClass` sont généralement appelées la `UpdateRegistry` fonction membre de la page de fabrique ou une propriété de la classe d’un contrôle.

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
Le handle d’instance du module associé à la classe du contrôle.

*clsid*<br/>
L’ID de classe unique du contrôle.

*pszProgID*<br/>
L’ID unique du programme du contrôle.

*idTypeName*<br/>
L’ID de ressource de la chaîne qui contient un nom de type lisible par l’utilisateur pour le contrôle.

*idBitmap*<br/>
L’ID de ressource de la bitmap utilisée pour représenter le contrôle OLE dans une barre d’outils ou de la palette.

*nRegFlags*<br/>
Contient un ou plusieurs des indicateurs suivants :

- `afxRegInsertable` Permet le contrôle s’affiche dans la boîte de dialogue Insérer un objet pour les objets OLE.

- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = apartment (cloisonné).

- `afxRegFreeThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = gratuit.

   Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = Both. Consultez [InprocServer32](/windows/desktop/com/inprocserver32) dans le SDK Windows pour plus d’informations sur l’inscription du modèle de thread.

> [!NOTE]
>  Dans les versions MFC antérieures 4.2 de MFC, la **int** *nRegFlags* paramètre était un paramètre de type BOOL, *bInsertable*, qui autorisé ou interdit le contrôle à insérer à partir de l’instruction Insert Boîte de dialogue d’objet.

*dwMiscStatus*<br/>
Contient un ou plusieurs des indicateurs d’état suivant (pour obtenir une description des indicateurs, consultez l’énumération OLEMISC dans le SDK Windows) :

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
Numéro de version secondaire de la classe de contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de contrôle a été inscrit ; sinon 0.

### <a name="remarks"></a>Notes

Cela permet au contrôle à utiliser par les conteneurs de contrôle OLE prenant en charge. `AfxOleRegisterControlClass` met à jour le Registre avec le nom du contrôle et l’emplacement sur le système et définit également le modèle de thread qui le contrôle prend en charge dans le Registre. Pour plus d’informations, consultez [technique Remarque 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), « Modèle de cloisonnement de thread dans OLE contrôles, » et [sur les processus et Threads](/windows/desktop/ProcThread/about-processes-and-threads) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

L’exemple ci-dessus montre comment `AfxOleRegisterControlClass` est appelée avec l’indicateur pour insérable et l’indicateur de cloisonnement or regroupés pour créer le sixième paramètre de modèle :

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

Le contrôle s’affichera dans la boîte de dialogue Insérer un objet pour les conteneurs activés, et il sera compatible avec le modèle de cloisonnement. Contrôles compatible avec le modèle de cloisonnement doivent garantir que les données sont protégées par des verrous, de classe statique afin que lorsqu’un contrôle dans un apartment (cloisonné) accède à des données statiques, elle n’est pas désactivée par le planificateur avant la fin de l’installation et une autre instance de la même classe démarre à l’aide les mêmes données statiques. Tout accès aux données statiques seront entourés par le code de section critique.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl.h

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
Le handle d’instance du module associé à la classe de page de propriétés.

*clsid*<br/>
ID de classe unique de la page de propriétés.

*idTypeName*<br/>
L’ID de ressource de la chaîne qui contient un nom lisible par l’utilisateur pour la page de propriétés.

*nRegFlags*<br/>
Peut contenir l’indicateur :

- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = apartment (cloisonné).

> [!NOTE]
>  Dans les versions MFC antérieures 4.2 de MFC, la **int** *nRegFlags* paramètre n’était pas disponible. Notez également que le `afxRegInsertable` indicateur n’est pas une option valide pour les pages de propriétés et provoque une assertion dans MFC s’il est défini

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de contrôle a été inscrit ; sinon 0.

### <a name="remarks"></a>Notes

Ainsi, la page de propriétés à utiliser par les conteneurs de contrôle OLE prenant en charge. `AfxOleRegisterPropertyPageClass` met à jour le Registre avec le nom de page de propriété et son emplacement sur le système et définit également le modèle de thread qui le contrôle prend en charge dans le Registre. Pour plus d’informations, consultez [technique Remarque 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), « Modèle de cloisonnement de thread dans OLE contrôles, » et [sur les processus et Threads](/windows/desktop/ProcThread/about-processes-and-threads) dans le SDK Windows.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl.h

##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib

Inscrit la bibliothèque de types avec la base de données d’inscription Windows et permet à la bibliothèque de types à utiliser par d’autres conteneurs qui sont de contrôle OLE prenant en charge.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Le handle d’instance de l’application associée à la bibliothèque de types.

*tlid*<br/>
ID unique de la bibliothèque de types.

*pszFileName*<br/>
Pointe vers le nom de fichier facultatif d’une bibliothèque de types localisée (. Fichier TLB) pour le contrôle.

*pszHelpDir*<br/>
Le nom du répertoire où vous pouvez trouver le fichier d’aide pour la bibliothèque de types. Si NULL, le fichier d’aide est censé pour se trouver dans le même répertoire que la bibliothèque de types lui-même.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la bibliothèque de types a été inscrit ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction met à jour le Registre avec le nom de bibliothèque de types et son emplacement sur le système.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass

Supprime l’entrée de classe de page de contrôle ou une propriété à partir de la base de données d’inscription Windows.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>Paramètres

*clsID*<br/>
L’ID de classe unique de la page de contrôle ou une propriété.

*pszProgID*<br/>
L’ID unique du programme de la page de contrôle ou une propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de page de contrôle ou une propriété a été correctement annulée ; sinon 0.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxctl.h

##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib

Appelez cette fonction pour supprimer l’entrée de bibliothèque de type de la base de données d’inscription Windows.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>Paramètres

*tlID*<br/>
ID unique de la bibliothèque de types.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la bibliothèque de types a été correctement annulée ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
