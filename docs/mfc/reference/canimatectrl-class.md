---
title: Classe CAnimateCtrl
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
ms.openlocfilehash: fcee569659d732c26e274c8ca189042a16f13557
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371063"
---
# <a name="canimatectrl-class"></a>Classe CAnimateCtrl

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
|[CAnimateCtrl::Fermer](#close)|Ferme le clip AVI.|
|[CAnimateCtrl::Créer](#create)|Crée un contrôle d’animation `CAnimateCtrl` et l’attache à un objet.|
|[CAnimateCtrl::CreateEx](#createex)|Crée un contrôle d’animation avec les styles `CAnimateCtrl` Windows étendus spécifiés et l’attache à un objet.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Indique si un clip Audio-Video Interleaved (AVI) est en lecture.|
|[CAnimateCtrl::Ouvert](#open)|Ouvre un clip AVI à partir d’un fichier ou d’une ressource et affiche la première image.|
|[CAnimateCtrl::Play](#play)|Joue le clip AVI sans son.|
|[CAnimateCtrl::Seek](#seek)|Affiche une seule image sélectionnée du clip AVI.|
|[CAnimateCtrl::Stop](#stop)|Arrête de jouer le clip AVI.|

## <a name="remarks"></a>Notes

Ce contrôle (et `CAnimateCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95, Windows 98, et Windows version NT 3.51 et plus tard.

Un contrôle d’animation est une fenêtre rectangulaire qui affiche un clip dans le format AVI (Audio Video Interleaved) — le format vidéo/audio Windows standard. Un clip AVI est une série de cadres bitmap, comme un film.

Les commandes d’animation ne peuvent lire que de simples clips AVI. Plus précisément, les clips à jouer par un contrôle d’animation doivent répondre aux exigences suivantes :

- Il doit y avoir exactement un flux vidéo et il doit avoir au moins un cadre.

- Il peut y avoir tout au plus deux flux dans le fichier (généralement l’autre flux, s’il est présent, est un flux audio, bien que le contrôle d’animation ignore les informations audio).

- Le clip doit être non compressé ou comprimé avec la compression RLE8.

- Aucun changement de palette n’est autorisé dans le flux vidéo.

Vous pouvez ajouter le clip AVI à votre application en tant que ressource AVI, ou il peut accompagner votre application comme un fichier AVI distinct.

Étant donné que votre thread continue d’exécuter pendant que le clip AVI est affiché, une utilisation courante pour un contrôle d’animation est d’indiquer l’activité du système pendant une longue opération. Par exemple, la boîte de dialogue Find de File Explorer affiche une loupe en mouvement lorsque le système recherche un fichier.

Si vous `CAnimateCtrl` créez un objet dans une boîte de dialogue ou à partir d’une ressource de dialogue à l’aide de l’éditeur de dialogue, il sera automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CAnimateCtrl` créez un objet à l’intérieur d’une fenêtre, vous devrez peut-être le détruire. Si vous `CAnimateCtrl` créez l’objet sur la pile, il est détruit automatiquement. Si vous `CAnimateCtrl` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire. Si vous retirez `CAnimateCtrl` une nouvelle classe et allouez `CAnimateCtrl` n’importe quelle mémoire dans cette classe, remplacez le destructeur pour disposer des allocations.

Pour plus d’informations sur l’utilisation `CAnimateCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation [CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl

Construit un objet `CAnimateCtrl`.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler la fonction membre [Créer](#create) avant de pouvoir effectuer d’autres opérations sur l’objet que vous créez.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Fermer

Ferme le clip AVI qui a été précédemment ouvert dans le contrôle d’animation (le cas échéant) et le supprime de la mémoire.

```
BOOL Close();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Créer

Crée un contrôle d’animation `CAnimateCtrl` et l’attache à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle d’animation. Appliquez toute combinaison des styles windows décrits dans la section Remarques ci-dessous et les styles de contrôle d’animation décrits dans [Les styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles) dans le SDK Windows.

*Rect*<br/>
Spécifie la position et la taille du contrôle d’animation. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog`du contrôle d’animation, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle d’animation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez un `CAnimateCtrl` en deux étapes. Tout d’abord, appelez le `Create`constructeur, puis appelez , ce `CAnimateCtrl` qui crée le contrôle d’animation et le fixe à l’objet.

Appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à un contrôle d’animation.

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

Si vous souhaitez utiliser des styles windows étendus avec `Create`votre contrôle d’animation, appelez [CreateEx](#createex) au lieu de .

En plus des styles de fenêtre énumérés ci-dessus, vous pouvez appliquer un ou plusieurs des styles de contrôle d’animation à un contrôle d’animation. Consultez le Windows SDK pour plus d’informations sur les [styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CAnimateCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du contrôle d’animation. Appliquez n’importe quelle combinaison de la fenêtre et des styles de contrôle d’animation décrits dans [Les styles de contrôle d’animation](/windows/win32/Controls/animation-control-styles) dans le SDK Windows.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::IsPlaying

Indique si un clip Audio-Video Interleaved (AVI) est en lecture.

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si un clip AVI est en lecture; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message ACM_ISPLAYING,](/windows/win32/Controls/acm-isplaying) qui est décrit dans le SDK Windows.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Ouvert

Appelez cette fonction pour ouvrir un clip AVI et afficher son premier cadre.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Objet `CString` ou pointeur d’une chaîne non terminée qui contient soit le nom du fichier AVI, soit le nom d’une ressource AVI. Si ce paramètre est NULL, le système ferme le clip AVI qui a été précédemment ouvert pour le contrôle d’animation, le cas échéant.

*nID*<br/>
L’identifiant de ressources AVI. Si ce paramètre est NULL, le système ferme le clip AVI qui a été précédemment ouvert pour le contrôle d’animation, le cas échéant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

La ressource AVI est chargée à partir du module qui a créé le contrôle d’animation.

`Open`ne prend pas en charge le son dans un clip AVI; vous ne pouvez ouvrir que des clips AVI silencieux.

Si le contrôle `ACS_AUTOPLAY` d’animation a le style, le contrôle d’animation commencera automatiquement à lire le clip immédiatement après qu’il l’ouvre. Il continuera à lire le clip en arrière-plan pendant que votre thread continue l’exécution. Lorsque le clip est fini de jouer, il sera automatiquement répété.

Si le contrôle `ACS_CENTER` d’animation a le style, le clip AVI sera centré dans le contrôle et la taille du contrôle ne changera pas. Si le contrôle d’animation n’a pas le `ACS_CENTER` style, le contrôle sera resized lorsque le clip AVI est ouvert à la taille des images dans le clip AVI. La position du coin supérieur gauche du contrôle ne changera pas, seulement la taille du contrôle.

Si le contrôle `ACS_TRANSPARENT` d’animation a le style, le premier cadre sera dessiné à l’aide d’un fond transparent plutôt que la couleur de fond spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::Play

Appelez cette fonction pour lire un clip AVI dans un contrôle d’animation.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Paramètres

*nDe*<br/>
Index à base zéro du cadre où le jeu commence. La valeur doit être inférieure à 65 536. Une valeur de 0 moyens commence par la première image du clip AVI.

*Nto*<br/>
Indice zéro du cadre où le jeu se termine. La valeur doit être inférieure à 65 536. Une valeur de - 1 signifie se terminer avec le dernier cadre dans le clip AVI.

*nRep*<br/>
Nombre de fois pour rejouer le clip AVI. Une valeur de - 1 signifie rejouer le fichier indéfiniment.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Le contrôle d’animation jouera le clip en arrière-plan pendant que votre thread continue à exécuter. Si le contrôle `ACS_TRANSPARENT` d’animation a du style, le clip AVI sera joué à l’aide d’un fond transparent plutôt que la couleur de fond spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Seek

Appelez cette fonction pour afficher statiquement un seul cadre de votre clip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Paramètres

*Nto*<br/>
Index zéro du cadre à afficher. La valeur doit être inférieure à 65 536. Une valeur de 0 signifie afficher la première image du clip AVI. Une valeur de -1 signifie afficher le dernier cadre du clip AVI.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Si le contrôle `ACS_TRANSPARENT` d’animation a du style, le clip AVI sera dessiné à l’aide d’un arrière-plan transparent plutôt que la couleur de fond spécifiée dans le clip d’animation.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Stop

Appelez cette fonction pour arrêter de jouer un clip AVI dans un contrôle d’animation.

```
BOOL Stop();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Créer](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
