---
title: CMetaFileDC (classe)
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 343ab1a5d0c38ab0d17c609fbfc134b144502553
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471810"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC (classe)

Implémente un métafichier Windows, qui contient une séquence de commandes SQL GDI (Graphics Device Interface) que vous pouvez relire pour créer une image ou du texte voulu.

## <a name="syntax"></a>Syntaxe

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construit un objet `CMetaFileDC`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Ferme le contexte de périphérique et crée un handle du métafichier.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Ferme un contexte de périphérique de métafichier amélioré et crée un handle du métafichier amélioré.|
|[CMetaFileDC::Create](#create)|Crée le contexte de périphérique de métafichier de Windows et l’attache à la `CMetaFileDC` objet.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crée un contexte de périphérique de métafichier pour un métafichier de format amélioré.|

## <a name="remarks"></a>Notes

Pour implémenter un métafichier Windows, commencez par créer un `CMetaFileDC` objet. Appeler le `CMetaFileDC` constructeur, puis appelez le [créer](#create) fonction membre, ce qui crée un contexte de périphérique de métafichier de Windows et l’attache à la `CMetaFileDC` objet.

Envoyez ensuite le `CMetaFileDC` la séquence de commandes de capture de données modifiées GDI que vous avez l’intention pour pouvoir les relire l’objet. Seules les commandes GDI qui créent de sortie, comme `MoveTo` et `LineTo`, peut être utilisé.

Une fois que vous avez envoyé les commandes souhaitées au métafichier, appelez le `Close` fonction membre, ce qui ferme les contextes de périphérique de métafichier et retourne un handle du métafichier. Puis de supprimer le `CMetaFileDC` objet.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) pouvez ensuite utiliser le handle du métafichier pour lire le métafichier à plusieurs reprises. Métafichier permettre également être manipulé par les fonctions de Windows comme [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea), qui copie un métafichier sur le disque.

Lorsque le métafichier n’est plus nécessaire, supprimez-le de la mémoire avec le [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) (fonction) Windows.

Vous pouvez également implémenter le `CMetaFileDC` objet afin qu’il puisse gérer les deux appels de sortie et attribut tel que les appels GDI `GetTextExtent`. Tel un métafichier est plus souple et plus facilement réemployer code général GDI, qui se compose souvent d’une combinaison d’appels de sortie et d’attribut. Le `CMetaFileDC` classe hérite des deux contextes de périphérique, `m_hDC` et `m_hAttribDC`, à partir de la capture de données modifiées. Le `m_hDC` contexte de périphérique gère toutes les [CDC](../../mfc/reference/cdc-class.md) GDI sortie des appels et le `m_hAttribDC` contexte de périphérique gère tous les appels d’attribut GDI de capture de données modifiées. En règle générale, les contextes de deux périphérique font référence au même appareil. Dans le cas de `CMetaFileDC`, le contrôleur de domaine de l’attribut est défini avec la valeur NULL par défaut.

Créer un deuxième contexte de périphérique qui pointe vers l’écran, une imprimante ou un appareil autre qu’un métafichier, puis appelez le `SetAttribDC` fonction membre pour associer le nouveau contexte de périphérique avec `m_hAttribDC`. Pour plus d’informations, les appels GDI seront désormais redirigées vers le nouveau `m_hAttribDC`. Sortie GDI appels ira à `m_hDC`, qui représente le métafichier.

Pour plus d’informations sur `CMetaFileDC`, consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAPTURE DE DONNÉES MODIFIÉES](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

Ferme le contexte de périphérique de métafichier et crée un handle de métafichier de Windows qui peut être utilisé pour lire le métafichier à l’aide de la [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) fonction membre.

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valeur de retour

Un HMETAFILE valide si la fonction a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Le handle du métafichier Windows peut également être permet de manipuler le métafichier avec des fonctions de Windows comme [CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea).

Supprimer le métafichier après utilisation en appelant le Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) (fonction).

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

Ferme un contexte de périphérique de métafichier amélioré et retourne un handle qui identifie un métafichier de format amélioré.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valeur de retour

Un handle d’un métafichier amélioré, en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Une application peut utiliser le handle de métafichier amélioré retourné par cette fonction pour effectuer les tâches suivantes :

- Afficher une image stockée dans un métafichier amélioré

- Créer des copies du métafichier amélioré

- Énumérer, modifier ou copier des enregistrements dans le métafichier amélioré

- Récupérer une description facultative du contenu du métafichier à partir de l’en-tête de métafichier amélioré

- Récupérer une copie de l’en-tête de métafichier amélioré

- Récupérer une copie binaire du métafichier amélioré

- Énumérer les couleurs de la palette facultative

- Convertir un métafichier de format amélioré dans un métafichier Windows-format

Lorsque l’application n’a plus besoin du handle du métafichier amélioré, il doit libérer le handle en appelant Win32 `DeleteEnhMetaFile` (fonction).

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

Construire un `CMetaFileDC` objet en deux étapes.

```
CMetaFileDC();
```

### <a name="remarks"></a>Notes

Tout d’abord, appelez `CMetaFileDC`, puis appelez `Create`, ce qui crée le contexte de périphérique de métafichier de Windows et l’attache à la `CMetaFileDC` objet.

##  <a name="create"></a>  CMetaFileDC::Create

Construire un `CMetaFileDC` objet en deux étapes.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFilename*<br/>
Pointe vers une chaîne de caractères se terminant par null. Spécifie le nom de fichier du métafichier à créer. Si *lpszFilename* est NULL, un métafichier en mémoire est créé.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Tout d’abord, appelez le constructeur `CMetaFileDC`, puis appelez `Create`, ce qui crée le contexte de périphérique de métafichier de Windows et l’attache à la `CMetaFileDC` objet.

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

Crée un contexte de périphérique pour un métafichier de format amélioré.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Paramètres

*pDCRef*<br/>
Identifie un appareil de référence pour le métafichier amélioré.

*lpszFileName*<br/>
Pointe vers une chaîne de caractères se terminant par null. Spécifie le nom de fichier pour le métafichier amélioré doit être créé. Si ce paramètre est NULL, le métafichier amélioré est basée sur la mémoire et son contenu perdu lorsque l’objet est détruit ou lorsque Win32 `DeleteEnhMetaFile` fonction est appelée.

*lpBounds*<br/>
Pointe vers un [RECT](../../mfc/reference/rect-structure1.md) structure de données ou un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui spécifie les dimensions en unités HIMETRIC (par incréments de.01-millimètre) de l’image à stocker dans le métafichier amélioré.

*lpszDescription*<br/>
Pointe vers une chaîne se terminant par zéro qui spécifie le nom de l’application qui a créé l’image, ainsi que le titre de l’image.

### <a name="return-value"></a>Valeur de retour

Un handle de contexte de périphérique de métafichier amélioré, en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Ce contrôleur de domaine peut être utilisé pour stocker une image indépendante du périphérique.

Windows utilise le périphérique de référence identifié par le *pDCRef* paramètre pour enregistrer la résolution et les unités de l’appareil sur lequel une image son état d’origine. Si le *pDCRef* paramètre est NULL, elle utilise le périphérique d’affichage actuel pour référence.

Les membres de gauche et supérieure de la `RECT` structure de données vers lequel pointe le *lpBounds* paramètre doit être plus petite que les membres de droite et en bas, respectivement. Points le long des bords du rectangle sont inclus dans l’image. Si *lpBounds* est NULL, l’interface graphique (GDI) calcule les dimensions du plus petit rectangle qui entoure l’image dessinée par l’application. Le *lpBounds* le paramètre doit être fourni lorsque cela est possible.

La chaîne pointée par le *lpszDescription* paramètre doit contenir un caractère null entre le nom de l’application et le nom de l’image et doit se terminer par deux caractères null — par exemple, « XYZ Graphics Editor\0Bald Eagle\0\0, « où \0 représente le caractère null. Si *lpszDescription* est NULL, il n’existe aucune entrée correspondante dans l’en-tête de métafichier amélioré.

Applications utilisent le contrôleur de domaine créé par cette fonction pour stocker une image de graphique dans un métafichier amélioré. Le handle de ce contrôleur de domaine peut être passé à n’importe quelle fonction GDI.

Une fois une application stocke une image dans un métafichier amélioré, il peut afficher l’image sur n’importe quel périphérique de sortie en appelant le `CDC::PlayMetaFile` (fonction). Lors de l’affichage de l’image, Windows utilise le rectangle vers lequel pointé le *lpBounds* paramètre et les données de résolution de l’appareil de référence pour positionner et de mettre à l’échelle de l’image. Le contexte de périphérique retourné par cette fonction contient les mêmes attributs par défaut associés à n’importe quel nouveau contrôleur de domaine.

Les applications doivent utiliser Win32 `GetWinMetaFileBits` fonction pour convertir un métafichier amélioré l’ancien format de métafichier de Windows.

Le nom de fichier pour le métafichier amélioré doit utiliser le. Extension EMF.

## <a name="see-also"></a>Voir aussi

[CDC, classe](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

