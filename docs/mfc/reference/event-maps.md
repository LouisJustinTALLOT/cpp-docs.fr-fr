---
title: Tables d'événements
ms.date: 06/20/2018
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: ef730574b26a4c3619df886b72770ce7e035a40e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916464"
---
# <a name="event-maps"></a>Tables d'événements

Chaque fois qu'un contrôle souhaite indiquer à son conteneur qu'une action (déterminée par le développeur du contrôle) s'est produite (par exemple une combinaison de touches, un clic du bouton de la souris ou une modification de l'état du contrôle), il appelle une fonction de déclenchement d'événement. Cette fonction notifie au conteneur de contrôle qu'une action importante s'est produite en déclenchant l'événement associé.

La bibliothèque MFC (Microsoft Foundation Class) offre un modèle de programmation optimisé pour déclencher des événements. Dans ce modèle, des "tables d'événements" sont utilisées pour indiquer quelles sont les fonctions qui déclenchent quels événements pour un contrôle donné. Les tables d'événements contiennent une macro pour chaque événement. Par exemple, une table d'événement qui déclenche un événement Clic pourrait se présenter comme suit :

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

La `EVENT_STOCK_CLICK` macro indique que le contrôle déclenchera un événement de clic sur une action chaque fois qu’il détecte un clic de souris. Pour obtenir une liste plus détaillée des autres événements stock, consultez l' [article contrôles ActiveX: Événements](../../mfc/mfc-activex-controls-events.md). Les macros sont également disponibles pour afficher les événements personnalisés.

Bien que les macros de table d'événements sont importantes, elles ne sont généralement pas insérées directement. Ceci est dû au fait que la fenêtre Propriétés crée automatiquement des entrées dans la table des événements de vos fichiers sources lorsque vous l'utilisez pour associer des fonctions de déclenchement d'événement avec des événements. Lorsque vous souhaitez modifier ou ajouter une entrée dans la table des événements, utilisez la fenêtre Propriétés.

Pour prendre en charge les tables d'événements, MFC fournit les macros suivantes :

## <a name="event-map-macros"></a>Macros de la table des événements

### <a name="event-map-declaration-and-demarcation"></a>Déclaration et démarcation de table d'événements

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Indique qu'une table d'événements est utilisée dans une classe pour faire correspondre les événements des fonctions de déclenchement d'événement (doit être utilisée dans la déclaration de classe).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Démarre la définition d'une table d'événements (doit être utilisée dans l'implémentation de classe).|
|[END_EVENT_MAP](#end_event_map)|Termine la définition d'une table d'événements (doit être utilisée dans l'implémentation de classe).|

### <a name="event-mapping-macros"></a>Macros de mappage d'événements

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Indique que la fonction de déclenchement d'événement déclenche l'événement spécifié.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Indique que la fonction de déclenchement d'événement déclenche l'événement spécifié, avec un ID de distribution indiqué.|

### <a name="message-mapping-macros"></a>Macros de mappage des messages

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Désigne un verbe personnalisé géré par le contrôle OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Remplace un mappage de verbe standard du contrôle OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

Chaque `COleControl`classe dérivée de votre programme peut fournir une table des événements pour spécifier les événements que votre contrôle doit déclencher.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_EVENT_MAP à la fin de votre déclaration de classe. Ensuite, dans le fichier. cpp qui définit les fonctions membres de la classe, utilisez la macro BEGIN_EVENT_MAP, les entrées de macro pour chacun des événements du contrôle et la macro END_EVENT_MAP pour déclarer la fin de la liste d’événements.

Pour plus d’informations sur les tables d’événements, [consultez l’article contrôles ActiveX: Événements](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl. h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Commence la définition de votre table d’événements.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe de contrôle dont se trouve la table d’événements.

*baseClass*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (. cpp) qui définit les fonctions membres pour votre classe, démarrez la table des événements avec la macro BEGIN_EVENT_MAP, puis ajoutez des entrées de macro pour chacun de vos événements et complétez la table des événements avec la macro END_EVENT_MAP.

Pour plus d’informations sur les tables d’événements et la macro BEGIN_EVENT_MAP, [consultez l’article contrôles ActiveX: Événements](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl. h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Utilisez la macro END_EVENT_MAP pour terminer la définition de votre table d’événements.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl. h

## <a name="event_custom"></a>  EVENT_CUSTOM

Définit une entrée de table d’événements pour un événement personnalisé.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*pszName*<br/>
Nom de l’événement.

*pfnFire*<br/>
Nom de la fonction de déclenchement d’événements.

*vtsParams*<br/>
Liste séparée par des espaces d’une ou de plusieurs constantes spécifiant la liste de paramètres de la fonction.

### <a name="remarks"></a>Notes

Le paramètre *vtsParams* est une liste de valeurs `VTS_` séparées par des espaces des constantes. Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

spécifie une liste contenant un entier 32 bits représentant une valeur de couleur RVB, suivi d’un pointeur vers `IFontDisp` l’interface d’un objet OLE font.

Les `VTS_` constantes et leurs significations sont les suivantes:

|Symbole|Type de paramètre|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|ACCÈS|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __char\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Des constantes variant supplémentaires ont été définies pour tous les types variant, à l’exception de VTS_FONT et VTS_PICTURE, qui fournissent un pointeur vers la constante de données Variant. Ces constantes sont nommées à `VTS_Pconstantname` l’aide de la Convention. Par exemple, VTS_PCOLOR est un pointeur vers une constante VTS_COLOR.

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl. h

## <a name="event_custom_id"></a>EVENT_CUSTOM_ID

Définit une fonction de déclenchement d’événements pour un événement personnalisé appartenant à l’ID de dispatch spécifié par *DISPID*.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Paramètres

*pszName*<br/>
Nom de l’événement.

*dispid*<br/>
ID de dispatch utilisé par le contrôle lors du déclenchement de l’événement.

*pfnFire*<br/>
Nom de la fonction de déclenchement d’événements.

*vtsParams*<br/>
Liste variable de paramètres passés au conteneur de contrôle lorsque l’événement est déclenché.

### <a name="remarks"></a>Notes

L’argument *vtsParams* est une liste de valeurs `VTS_` séparées par des espaces des constantes. Une ou plusieurs de ces valeurs, séparées par des espaces, et non par des virgules, spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

spécifie une liste contenant un entier 32 bits représentant une valeur de couleur RVB, suivi d’un pointeur vers `IFontDisp` l’interface d’un objet OLE font.

Pour obtenir la `VTS_` liste des constantes, consultez [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl. h

## <a name="on_oleverb"></a>ON_OLEVERB

Cette macro définit une entrée de la table des messages qui mappe un verbe personnalisé à une fonction membre spécifique de votre contrôle.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*idsVerbName*<br/>
ID de ressource de chaîne du nom du verbe.

*memberFxn*<br/>
Fonction appelée par le Framework lorsque le verbe est appelé.

### <a name="remarks"></a>Notes

L’éditeur de ressources peut être utilisé pour créer des noms de verbes personnalisés qui sont ajoutés à votre table de chaînes.

Le prototype de fonction pour *memberFxn* est:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Les valeurs des paramètres *lpMsg*, *hwndParent*et *lpRect* sont extraites des paramètres correspondants de la `IOleObject::DoVerb` fonction membre.

### <a name="requirements"></a>Configuration requise

**En-tête** AFXOLE. h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

Utilisez cette macro pour remplacer le comportement par défaut d’un verbe standard.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Index de verbe standard pour le verbe en cours de substitution.

*memberFxn*<br/>
Fonction appelée par le Framework lorsque le verbe est appelé.

### <a name="remarks"></a>Notes

L’index de verbe standard est de la `OLEIVERB_`forme, suivi d’une action. OLEIVERB_SHOW, OLEIVERB_HIDE et OLEIVERB_UIACTIVATE sont des exemples de verbes standard.

Pour obtenir une description du prototype de fonction à utiliser comme paramètre *memberFxn* , consultez [ON_OLEVERB](#on_oleverb) .

### <a name="requirements"></a>Configuration requise

**En-tête** AFXOLE. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
