---
title: Tables d'événements
ms.date: 06/20/2018
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: 98614aa41d3131d28c9e0c7584e5a88c2249ef97
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612237"
---
# <a name="event-maps"></a>Tables d'événements

Chaque fois qu'un contrôle souhaite indiquer à son conteneur qu'une action (déterminée par le développeur du contrôle) s'est produite (par exemple une combinaison de touches, un clic du bouton de la souris ou une modification de l'état du contrôle), il appelle une fonction de déclenchement d'événement. Cette fonction notifie au conteneur de contrôle qu'une action importante s'est produite en déclenchant l'événement associé.

La bibliothèque MFC (Microsoft Foundation Class) offre un modèle de programmation optimisé pour déclencher des événements. Dans ce modèle, des "tables d'événements" sont utilisées pour indiquer quelles sont les fonctions qui déclenchent quels événements pour un contrôle donné. Les tables d'événements contiennent une macro pour chaque événement. Par exemple, une table d'événement qui déclenche un événement Clic pourrait se présenter comme suit :

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Le `EVENT_STOCK_CLICK` macro indique que le contrôle déclenche un événement chaque fois qu’il détecte une souris cliquez stock. Pour obtenir une liste plus détaillée d’autres événements stock, consultez l’article [contrôles ActiveX : Événements](../../mfc/mfc-activex-controls-events.md). Les macros sont également disponibles pour afficher les événements personnalisés.

Bien que les macros de table d'événements sont importantes, elles ne sont généralement pas insérées directement. Ceci est dû au fait que la fenêtre Propriétés crée automatiquement des entrées dans la table des événements de vos fichiers sources lorsque vous l'utilisez pour associer des fonctions de déclenchement d'événement avec des événements. Lorsque vous souhaitez modifier ou ajouter une entrée dans la table des événements, utilisez la fenêtre Propriétés.

Pour prendre en charge les tables d'événements, MFC fournit les macros suivantes :

## <a name="event-map-macros"></a>Macros de mappage d’événement

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

Chaque `COleControl`-classe dérivée dans votre programme peut fournir une table d’événements pour spécifier les événements que votre contrôle se déclenche.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Utilisez le declare_event_map (macro) à la fin de votre déclaration de classe. Puis, dans le fichier .cpp qui définit les fonctions membres pour la classe, utilisez le begin_event_map (macro), les entrées de la macro pour chacun des événements du contrôle et l’end_event_map (macro) pour déclarer la fin de la liste des événements.

Pour plus d’informations sur les tables d’événements, consultez l’article [contrôles ActiveX : Événements](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Commence la définition de votre table d’événements.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe de contrôle dont l’événement mapper.

*baseClass*<br/>
Spécifie le nom de la classe de base de *theClass*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrez la table d’événements avec le begin_event_map (macro), puis ajouter des entrées de macro pour chacun de vos événements et terminer la table d’événements avec l’end_event_map (macro).

Pour plus d’informations sur les tables d’événements et le begin_event_map (macro), consultez l’article [contrôles ActiveX : Événements](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Utilisez l’end_event_map (macro) à la fin de la définition de votre table d’événements.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM

Définit une entrée de table d’événements pour un événement personnalisé.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*pszName*<br/>
Nom de l’événement.

*pfnFire*<br/>
Le nom de l’événement de fonction de déclenchement.

*vtsParams*<br/>
Une liste séparée par des espaces d’une ou plusieurs constantes spécifiant la liste des paramètres de la fonction.

### <a name="remarks"></a>Notes

Le *vtsParams* paramètre est une liste séparée par des espaces de valeurs à partir de la `VTS_` constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Spécifie une liste contenant un entier 32 bits représentant RVB de couleur, suivi par un pointeur vers le `IFontDisp` interface d’un objet de police OLE.

Le `VTS_` constantes et leurs significations sont comme suit :

|Symbole|Type de paramètre|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|DEVISE|
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
> Les constantes de type variants supplémentaires ont été définis pour tous les types variants, à l’exception VTS_FONT et VTS_PICTURE, qui fournissent un pointeur vers la constante de données variant. Ces constantes sont nommés à l’aide de la `VTS_Pconstantname` convention. Par exemple, VTS_PCOLOR est un pointeur vers un VTS_COLOR (constante).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

Définit un événement de déclenchement de fonction d’un événement personnalisé qui appartiennent à l’ID de dispatch spécifié par *dispid*.

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
ID de distribution utilisé par le contrôle lors du déclenchement de l’événement.

*pfnFire*<br/>
Le nom de l’événement de fonction de déclenchement.

*vtsParams*<br/>
Une liste de variables de paramètres transmis au conteneur du contrôle lorsque l’événement est déclenché.

### <a name="remarks"></a>Notes

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la `VTS_` constantes. Un ou plusieurs de ces valeurs séparées par des espaces, et non par des virgules, spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Spécifie une liste contenant un entier 32 bits représentant RVB de couleur, suivi par un pointeur vers le `IFontDisp` interface d’un objet de police OLE.

Pour obtenir la liste de la `VTS_` constantes, consultez [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Configuration requise

**En-tête** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

Cette macro définit une entrée de mappage de message qui mappe un verbe personnalisé à une fonction membre spécifique de votre contrôle.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*idsVerbName*<br/>
L’ID de ressource de chaîne du nom du verbe.

*memberFxn*<br/>
La fonction appelée par le framework lorsque le verbe est appelé.

### <a name="remarks"></a>Notes

L’éditeur de ressources peut être utilisé pour créer des noms de verbe personnalisées qui sont ajoutés à votre table de chaînes.

Le prototype de fonction pour *memberFxn* est :

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Les valeurs de la *lpMsg*, *hWndParent*, et *lpRect* paramètres proviennent de paramètres correspondants de la `IOleObject::DoVerb` fonction membre.

### <a name="requirements"></a>Configuration requise

**En-tête** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

Utilisez cette macro pour remplacer le comportement par défaut d’un verbe standard.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Index du verbe standard pour le verbe qui est substitué.

*memberFxn*<br/>
La fonction appelée par le framework lorsque le verbe est appelé.

### <a name="remarks"></a>Notes

L’index du verbe standard est au format `OLEIVERB_`, suivi par une action. OLEIVERB_SHOW, OLEIVERB_HIDE et OLEIVERB_UIACTIVATE sont quelques exemples de verbes standard.

Consultez [ON_OLEVERB](#on_oleverb) pour obtenir une description du prototype de fonction à utiliser comme la *memberFxn* paramètre.

### <a name="requirements"></a>Configuration requise

**En-tête** afxole.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
