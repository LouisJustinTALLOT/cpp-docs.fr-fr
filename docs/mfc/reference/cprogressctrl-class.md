---
title: CProgressCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: c5eb6a93cd68c2dafb76af3b0e42da8b56566e25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364005"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl, classe

Fournit les fonctionnalités du contrôle commun de barre de progression Windows.

## <a name="syntax"></a>Syntaxe

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construit un objet `CProgressCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CProgressCtrl::Créer](#create)|Crée un contrôle de barre de `CProgressCtrl` progression et l’attache à un objet.|
|[CProgressCtrl::CreateEx](#createex)|Crée un contrôle de progression avec les styles `CProgressCtrl` Windows étendus spécifiés et l’attache à un objet.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtient la couleur de la barre d’indicateur de progression pour le contrôle actuel de barre de progression.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtient la couleur de fond de la barre de progression actuelle.|
|[CProgressCtrl::GetPos](#getpos)|Obtient la position actuelle de la barre de progression.|
|[CProgressCtrl::GetRange](#getrange)|Obtient les limites inférieures et supérieures de la portée du contrôle de la barre de progression.|
|[CProgressCtrl::GetState](#getstate)|Obtient l’état du contrôle actuel de la barre de progression.|
|[CProgressCtrl::GetStep](#getstep)|Récupère l’augmentation de l’étape pour la barre de progression du contrôle actuel de la barre de progression.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Avance la position actuelle d’un contrôle de barre de progression par une incrément spécifiée et redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Définit la couleur de la barre de l’indicateur de progression dans le contrôle actuel de la barre de progression.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Définit la couleur de fond pour la barre de progression.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Tourne le mode chapiteau allumé ou éteint pour le contrôle actuel de la barre de progression.|
|[CProgressCtrl::SetPos](#setpos)|Définit la position actuelle pour un contrôle de barre de progression et redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl::SetRange](#setrange)|Définit les plages minimales et maximales pour un contrôle de barre de progression et redessine la barre pour refléter les nouvelles gammes.|
|[CProgressCtrl::SetState](#setstate)|Définit l'état du contrôle de barre de progression actuel.|
|[CProgressCtrl::SetStep](#setstep)|Spécifie l’incrément de l’étape pour un contrôle de barre de progression.|
|[CProgressCtrl::StepIt](#stepit)|Avance la position actuelle pour un contrôle de barre de progression par l’incrément d’étape (voir [SetStep](#setstep)) et redessine la barre pour refléter la nouvelle position.|

## <a name="remarks"></a>Notes

Un contrôle de la barre de progression est une fenêtre qu’une application peut utiliser pour indiquer l’avancement d’une longue opération. Il se compose d’un rectangle qui est progressivement rempli, de gauche à droite, avec le système mettre en évidence la couleur comme une opération progresse.

Un contrôle de barre de progression a une portée et une position actuelle. La plage représente la durée totale de l’opération, et la position actuelle représente les progrès réalisés par l’application pour terminer l’opération. La procédure de fenêtre utilise la portée et la position actuelle pour déterminer le pourcentage de la barre de progression pour remplir avec la couleur de surbrillance. Étant donné que la fourchette et les valeurs de position actuelles sont exprimées comme des intégraires signés, la fourchette possible des valeurs de position actuelles est de -2 147 483 648 à 2 147 483 647 inclusivement.

Pour plus d’informations sur l’utilisation `CProgressCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

Construit un objet `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Notes

Après la `CProgressCtrl` construction de `CProgressCtrl::Create` l’objet, appelez pour créer le contrôle de la barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::Créer

Crée un contrôle de barre de `CProgressCtrl` progression et l’attache à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle de la barre de progression. Appliquer toute combinaison de styles de fenêtre attribués dans [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows, en plus des styles de contrôle de barres de progression suivants, au contrôle:

- PBS_VERTICAL affiche l’information de progression verticalement, de haut en bas. Sans ce drapeau, le contrôle de la barre de progression affiche horizontalement, de gauche à droite.

- PBS_SMOOTH affiche un remplissage progressif et lisse dans le contrôle de la barre de progression. Sans ce drapeau, le contrôle se remplira de blocs.

*Rect*<br/>
Spécifie la taille et la position du contrôle de la barre de progression. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/previous-versions/dd162897\(v=vs.85\)) Étant donné que le contrôle doit être une fenêtre pour enfants, les coordonnées spécifiées sont relatives à la zone client du *pParentWnd*.

*pParentWnd*<br/>
Spécifie la fenêtre parente du `CDialog`contrôle de la barre de progression, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de la barre de progression.

### <a name="return-value"></a>Valeur de retour

VRAI si `CProgressCtrl` l’objet est créé avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Vous construisez un `CProgressCtrl` objet en deux étapes. Tout d’abord, appelez le `CProgressCtrl` constructeur, qui `Create`crée l’objet, puis appelez , ce qui crée le contrôle de la barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CProgressCtrl` et l’associe à l’objet.

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
Spécifie le style du contrôle de la barre de progression. Appliquez toute combinaison de styles de fenêtre décrits dans [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

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

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::GetBarColor

Obtient la couleur de la barre d’indicateur de progression pour le contrôle actuel de barre de progression.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de la barre de progression actuelle, représentée comme une valeur [COLORREF,](/windows/win32/gdi/colorref) ou CLR_DEFAULT si la couleur de barre de l’indicateur de progression est la couleur par défaut.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PBM_GETBARCOLOR,](/windows/win32/Controls/pbm-getbarcolor) qui est décrit dans le SDK Windows.

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

Obtient la couleur de fond de la barre de progression actuelle.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de fond de la barre de progression actuelle, représentée comme une valeur [COLORREF.](/windows/win32/gdi/colorref)

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PBM_GETBKCOLOR,](/windows/win32/Controls/pbm-getbkcolor) qui est décrit dans le SDK Windows.

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::GetPos

Récupère la position actuelle de la barre de progression.

```
int GetPos();
```

### <a name="return-value"></a>Valeur de retour

La position du contrôle de la barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de la barre de progression n’est pas l’emplacement physique sur l’écran, mais se situe plutôt entre la plage supérieure et inférieure indiquée dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl::GetRange

Obtient les limites inférieures et supérieures actuelles, ou la portée, du contrôle de la barre de progression.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower (en)*<br/>
Une référence à un intégrant recevant la limite inférieure du contrôle de la barre de progression.

*nUpper (en)*<br/>
Une référence à un intégrant recevant la limite supérieure du contrôle de la barre de progression.

### <a name="remarks"></a>Notes

Cette fonction copie les valeurs des limites inférieures et supérieures aux intégraux référencés par *nLower* et *nUpper*, respectivement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::GetState

Obtient l’état du contrôle actuel de la barre de progression.

```
int GetState() const;
```

### <a name="return-value"></a>Valeur de retour

L’état du contrôle actuel des barres de progression, qui est l’une des valeurs suivantes :

|Value|State|
|-----------|-----------|
|PBST_NORMAL|En cours|
|PBST_ERROR|Error|
|PBST_PAUSED|Suspendu|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PBM_GETSTATE,](/windows/win32/Controls/pbm-getstate) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’état du contrôle actuel de la barre de progression.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl::GetStep

Récupère l’augmentation de l’étape pour la barre de progression du contrôle actuel de la barre de progression.

```
int GetStep() const;
```

### <a name="return-value"></a>Valeur de retour

L’augmentation de l’étape de la barre de progression.

### <a name="remarks"></a>Notes

L’augmentation de l’étape est le montant par lequel un appel à [CProgressCtrl::StepIt](#stepit) augmente la position actuelle de la barre de progression.

Cette méthode envoie le [message PBM_GETSTEP,](/windows/win32/Controls/pbm-getstep) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’incrément d’étape du contrôle actuel de la barre de progression.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::OffsetPos

Avance la position actuelle du contrôle de la barre de progression par l’incrément spécifié par *les NPos* et redessine la barre pour refléter la nouvelle position.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Montant pour faire avancer la position.

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de la barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::SetBarColor

Définit la couleur de la barre de l’indicateur de progression dans le contrôle actuel de la barre de progression.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*clrBar*|[dans] Une valeur [COLORREF](/windows/win32/gdi/colorref) qui spécifie la nouvelle couleur de la barre de l’indicateur de progression. Spécifiez CLR_DEFAULT pour faire en sorte que la barre de progression utilise sa couleur par défaut.|

### <a name="return-value"></a>Valeur de retour

La couleur précédente de la barre de l’indicateur de progression, représentée comme une valeur [COLORREF,](/windows/win32/gdi/colorref) ou CLR_DEFAULT si la couleur de la barre de l’indicateur de progression est la couleur par défaut.

### <a name="remarks"></a>Notes

La `SetBarColor` méthode ne définit la couleur de la barre de progression que si un [thème](/windows/win32/Controls/visual-styles-overview) Windows Vista n’est pas en vigueur.

Cette méthode envoie le [message PBM_SETBARCOLOR,](/windows/win32/Controls/pbm-setbarcolor) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie la couleur de la barre de progression en rouge, vert, bleu, ou par défaut.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

Définit la couleur de fond pour la barre de progression.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Paramètres

*clrNew*<br/>
Une valeur COLORREF qui spécifie la nouvelle couleur de fond. Spécifiez la valeur CLR_DEFAULT d’utiliser la couleur de fond par défaut pour la barre de progression.

### <a name="return-value"></a>Valeur de retour

La valeur [COLORREF](/windows/win32/gdi/colorref) indiquant la couleur de fond précédente, ou CLR_DEFAULT si la couleur de fond est la couleur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

Tourne le mode chapiteau allumé ou éteint pour le contrôle actuel de la barre de progression.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fMarqueeMode*|[dans] VRAI pour activer le mode chapiteau, ou FALSE pour désactiver le mode chapiteau.|
|*nInterval (en)*|[dans] Temps en millisecondes entre les mises à jour de l’animation de chapiteau.|

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie toujours VRAI.

### <a name="remarks"></a>Notes

Lorsque le mode chapiteau est activé, la barre de progression est animée et défile comme un panneau sur un chapiteau de théâtre.

Cette méthode envoie le [message PBM_SETMARQUEE,](/windows/win32/Controls/pbm-setmarquee) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant commence et arrête l’animation de défilement de chapiteau.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

Définit la position actuelle du contrôle de la barre de progression comme spécifié par *nPos* et redessine la barre pour refléter la nouvelle position.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Nouvelle position du contrôle de la barre de progression.

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de la barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de la barre de progression n’est pas l’emplacement physique sur l’écran, mais se situe plutôt entre la plage supérieure et inférieure indiquée dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::SetRange

Définit les limites supérieures et inférieures de la portée du contrôle de la barre de progression et redessine la barre pour refléter les nouvelles plages.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower (en)*<br/>
Spécifie la limite inférieure de la plage (par défaut est nulle).

*nUpper (en)*<br/>
Spécifie la limite supérieure de la plage (par défaut est de 100).

### <a name="remarks"></a>Notes

La fonction `SetRange32` membre définit la plage 32 bits pour le contrôle de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::SetState

Définit l'état du contrôle de barre de progression actuel.

```
int SetState(int iState);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iState (États-Unis)*|[dans] L’État de fixer la barre de progression. Utilisez l’une des valeurs suivantes :<br /><br /> - PBST_NORMAL - En cours<br />- PBST_ERROR - Erreur<br />- PBST_PAUSED - Pause|

### <a name="return-value"></a>Valeur de retour

État précédent du contrôle de barre de progression actuel.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message PBM_SETSTATE,](/windows/win32/Controls/pbm-setstate) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L'exemple de code suivant attribue au contrôle de barre de progression actuel l'état En pause ou Suspendu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::SetStep

Spécifie l’incrément de l’étape pour un contrôle de barre de progression.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Paramètres

*nStep (en)*<br/>
Nouvelle augmentation de l’étape.

### <a name="return-value"></a>Valeur de retour

L’augmentation de l’étape précédente.

### <a name="remarks"></a>Notes

L’augmentation de l’étape est le `CProgressCtrl::StepIt` montant par lequel un appel pour augmenter la position actuelle de la barre de progression.

L’augmentation par défaut de l’étape est de 10.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::StepIt

Avance la position actuelle pour un contrôle de barre de progression par l’incrément d’étape et redessine la barre pour refléter la nouvelle position.

```
int StepIt();
```

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de la barre de progression.

### <a name="remarks"></a>Notes

L’incrément d’étape `CProgressCtrl::SetStep` est fixé par la fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
