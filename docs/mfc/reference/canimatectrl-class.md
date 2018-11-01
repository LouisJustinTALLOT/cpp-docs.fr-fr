---
title: CAnimateCtrl (classe)
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: 5bbd59101815d18cae92b9996aff54f0cadaf9ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608427"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl (classe)

Fournit les fonctionnalités du contrôle commun d'animation Windows.

## <a name="syntax"></a>Syntaxe

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construit un objet `CAnimateCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|Ferme le clip AVI.|
|[CAnimateCtrl::Create](#create)|Crée un contrôle animation et l’attache à un `CAnimateCtrl` objet.|
|[CAnimateCtrl::CreateEx](#createex)|Crée un contrôle animation avec les styles étendus Windows spécifiés et l’attache à un `CAnimateCtrl` objet.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Indique si un clip Audio-Video Interleaved (AVI) en cours de lecture.|
|[CAnimateCtrl::Open](#open)|Ouvre un clip AVI à partir d’un fichier ou une ressource et affiche la première image.|
|[CAnimateCtrl::Play](#play)|Permet de lire le clip AVI sans le son.|
|[CAnimateCtrl::Seek](#seek)|Affiche un frame unique sélectionné du clip AVI.|
|[CAnimateCtrl::Stop](#stop)|Arrête la lecture du clip AVI.|

## <a name="remarks"></a>Notes

Ce contrôle (et par conséquent la `CAnimateCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95, Windows 98 et Windows NT version 3.51 et ultérieures.

Un contrôle animation est une fenêtre rectangulaire qui affiche un clip au format AVI (Audio Video Interleaved), le format audio/vidéo Windows standard. Un clip AVI est une série de frames bitmap, comme un film.

Contrôles d’animation peuvent lire uniquement les éléments AVI simples. Plus précisément, les éléments pour être lues par un contrôle animation doivent remplir les conditions suivantes :

- Il doit y avoir exactement un seul flux vidéo et il doit avoir au moins un frame.

- Il peut y avoir au plus deux flux de données dans le fichier (l’autre flux, le cas échéant, est généralement un flux audio, bien que le contrôle d’animation ignore les informations audio).

- L’élément doit être décompressé ou compressé avec la compression RLE8.

- Aucune modification de la palette est autorisée dans le flux vidéo.

Vous pouvez ajouter le clip AVI à votre application comme une ressource AVI, ou elle peut accompagner votre application sous la forme d’un fichier AVI distinct.

Étant donné que votre thread continue de s’exécuter pendant que le clip AVI s’affiche, une utilisation courante d’un contrôle animation consiste à indiquer l’activité du système pendant une longue opération. Par exemple, la boîte de dialogue Rechercher de l’Explorateur de fichiers affiche une loupe qui se déplace en tant que le système recherche un fichier.

Si vous créez un `CAnimateCtrl` de l’objet au sein d’une boîte de dialogue zone ou à partir d’une ressource de boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue, il sera automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CAnimateCtrl` de l’objet dans une fenêtre, vous devrez peut-être à détruire. Si vous créez le `CAnimateCtrl` de l’objet sur la pile, il est supprimé automatiquement. Si vous créez le `CAnimateCtrl` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet à détruire. Si vous dérivez une nouvelle classe à partir de `CAnimateCtrl` et allouer de mémoire dans cette classe, substituez le `CAnimateCtrl` destructeur pour supprimer des allocations.

Pour plus d’informations sur l’utilisation de `CAnimateCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl

Construit un objet `CAnimateCtrl`.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler la [créer](#create) fonction membre avant d’effectuer d’autres opérations sur l’objet que vous créez.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>  CAnimateCtrl::Close

Ferme le clip AVI qui a été précédemment ouvert dans le contrôle d’animation (le cas échéant) et le supprime de la mémoire.

```
BOOL Close();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

##  <a name="create"></a>  CAnimateCtrl::Create

Crée un contrôle animation et l’attache à un `CAnimateCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de l’animation. Appliquer n’importe quelle combinaison de windows décrits dans la section Notes ci-dessous et les styles de contrôle d’animation de styles décrit dans [Styles de contrôle d’Animation](/windows/desktop/Controls/animation-control-styles) dans le SDK Windows.

*Rect*<br/>
Spécifie la position et la taille du contrôle d’animation. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](../../mfc/reference/rect-structure1.md) structure.

*pParentWnd*<br/>
Spécifie l’animation fenêtre du contrôle parent, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de l’animation

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez un `CAnimateCtrl` en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle d’animation et l’attache à la `CAnimateCtrl` objet.

Appliquer les éléments suivants [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à un contrôle de l’animation.

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

Si vous souhaitez utiliser des styles étendus windows avec votre contrôle de l’animation, appelez [CreateEx](#createex) au lieu de `Create`.

Outre les styles de fenêtre répertoriées ci-dessus, vous souhaiterez appliquer une ou plusieurs des styles de contrôle d’animation à un contrôle de l’animation. Consultez le Kit de développement logiciel Windows pour plus d’informations sur [styles de contrôle d’animation](/windows/desktop/Controls/animation-control-styles).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

##  <a name="createex"></a>  CAnimateCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe le `CAnimateCtrl` objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de l’animation. Appliquer n’importe quelle combinaison de la fenêtre et de styles de contrôle d’animation décrit dans [Styles de contrôle d’Animation](/windows/desktop/Controls/animation-control-styles) dans le SDK Windows.

*Rect*<br/>
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

Indique si un clip Audio-Video Interleaved (AVI) en cours de lecture.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si un clip AVI est lu ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying) message, qui est décrite dans le SDK Windows.

##  <a name="open"></a>  CAnimateCtrl::Open

Appelez cette fonction pour un clip AVI s’ouvre et affiche sa première image.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Un `CString` objet ou un pointeur vers une chaîne se terminant par null qui contient le nom du fichier AVI ou le nom d’une ressource AVI. Si ce paramètre est NULL, le système ferme le clip AVI qui a été ouvert précédemment pour le contrôle d’animation, le cas échéant.

*nID*<br/>
L’identificateur de ressource AVI. Si ce paramètre est NULL, le système ferme le clip AVI qui a été ouvert précédemment pour le contrôle d’animation, le cas échéant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

La ressource AVI est chargée à partir du module qui a créé le contrôle de l’animation.

`Open` ne prend pas en charge son dans un clip AVI ; Vous pouvez ouvrir uniquement les éléments AVI en mode silencieux.

Si le contrôle de l’animation a le `ACS_AUTOPLAY` style, le contrôle d’animation démarre automatiquement la lecture de l’élément immédiatement après, il s’ouvre. Il continue à lire le clip en arrière-plan pendant que votre thread continue de s’exécuter. Lorsque l’élément est terminé pour la lecture, il sera automatiquement être répétée.

Si le contrôle de l’animation a le `ACS_CENTER` style, le clip AVI sera centré dans le contrôle et la taille du contrôle ne change pas. Si le contrôle d’animation n’a pas la `ACS_CENTER` style, le contrôle doit être redimensionné lorsque le clip AVI est ouvert à la taille des images dans le clip AVI. La position de l’angle supérieur gauche du contrôle changera pas, uniquement la taille du contrôle.

Si le contrôle de l’animation a le `ACS_TRANSPARENT` style, la première image sera dessinée à l’aide d’un arrière-plan transparent au lieu de la couleur d’arrière-plan spécifiée dans l’élément d’animation.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

##  <a name="play"></a>  CAnimateCtrl::Play

Appelez cette fonction pour lire un clip AVI dans un contrôle animation.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Paramètres

*Ndepuis*<br/>
Index de base zéro de l’image où la lecture commence. Valeur doit être inférieure à 65 536. Valeur 0 signifie commence par la première image dans le clip AVI.

*nPour*<br/>
Index de base zéro de l’image où lecture se termine. Valeur doit être inférieure à 65 536. Une valeur de - 1 signifie que de se terminer par la dernière image dans le clip AVI.

*nRep*<br/>
Nombre de fois pour relire le clip AVI. Une valeur de - 1 signifie que le fichier de relecture indéfiniment.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Le contrôle d’animation jouera le clip en arrière-plan pendant que votre thread continue de s’exécuter. Si le contrôle de l’animation a `ACS_TRANSPARENT` style, le clip AVI est lu à l’aide d’un arrière-plan transparent, plutôt que la couleur d’arrière-plan spécifiée dans l’élément d’animation.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

##  <a name="seek"></a>  CAnimateCtrl::Seek

Appelez cette fonction pour afficher statiquement une seule image de votre clip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Paramètres

*nPour*<br/>
Index de base zéro de l’image à afficher. Valeur doit être inférieure à 65 536. La valeur 0 signifie qu’affiche la première image dans le clip AVI. La valeur -1 signifie qu’affiche la dernière image dans le clip AVI.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si le contrôle de l’animation a `ACS_TRANSPARENT` style, le clip AVI sera dessiné à l’aide d’un arrière-plan transparent au lieu de la couleur d’arrière-plan spécifiée dans l’élément d’animation.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

##  <a name="stop"></a>  CAnimateCtrl::Stop

Appelez cette fonction pour arrêter la lecture d’un clip AVI dans un contrôle animation.

```
BOOL Stop();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)

