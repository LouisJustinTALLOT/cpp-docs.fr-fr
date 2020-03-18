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
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421533"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl, classe

Fournit les fonctionnalités du contrôle commun de barre de progression Windows.

## <a name="syntax"></a>Syntaxe

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CProgressCtrl :: CProgressCtrl](#cprogressctrl)|Construit un objet `CProgressCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CProgressCtrl :: Create](#create)|Crée un contrôle de barre de progression et l’attache à un objet `CProgressCtrl`.|
|[CProgressCtrl :: CreateEx](#createex)|Crée un contrôle de progression avec les styles étendus Windows spécifiés et l’attache à un objet `CProgressCtrl`.|
|[CProgressCtrl :: GetBarColor](#getbarcolor)|Obtient la couleur de la barre de l’indicateur de progression pour le contrôle de barre de progression actuel.|
|[CProgressCtrl :: GetBkColor](#getbkcolor)|Obtient la couleur d’arrière-plan de la barre de progression actuelle.|
|[CProgressCtrl :: GetPos](#getpos)|Obtient la position actuelle de la barre de progression.|
|[CProgressCtrl :: GetRange](#getrange)|Obtient les limites inférieure et supérieure de la plage du contrôle de barre de progression.|
|[CProgressCtrl :: GetState](#getstate)|Obtient l’état du contrôle de barre de progression actuel.|
|[CProgressCtrl :: GetStep](#getstep)|Récupère l’incrément de l’étape pour la barre de progression du contrôle de barre de progression actuel.|
|[CProgressCtrl :: OffsetPos](#offsetpos)|Avance la position actuelle d’un contrôle de barre de progression d’un incrément spécifié et redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl :: SetBarColor](#setbarcolor)|Définit la couleur de la barre de l’indicateur de progression dans le contrôle de barre de progression actuel.|
|[CProgressCtrl :: SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan de la barre de progression.|
|[CProgressCtrl :: SetMarquee](#setmarquee)|Active ou désactive le mode texte défilant pour le contrôle de barre de progression actuel.|
|[CProgressCtrl :: SetPos](#setpos)|Définit la position actuelle pour un contrôle de barre de progression et redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl :: SetRange](#setrange)|Définit les plages minimale et maximale pour un contrôle de barre de progression et redessine la barre pour refléter les nouvelles plages.|
|[CProgressCtrl :: SetState](#setstate)|Définit l'état du contrôle de barre de progression actuel.|
|[CProgressCtrl :: SetStep](#setstep)|Spécifie l’incrément de l’étape pour un contrôle de barre de progression.|
|[CProgressCtrl :: StepIt](#stepit)|Avance la position actuelle d’un contrôle de barre de progression par l’incrément de l’étape (consultez [SetStep](#setstep)) et redessine la barre pour refléter la nouvelle position.|

## <a name="remarks"></a>Notes

Un contrôle de barre de progression est une fenêtre qu’une application peut utiliser pour indiquer la progression d’une opération de longue durée. Il se compose d’un rectangle qui est progressivement rempli, de gauche à droite, avec la couleur de mise en surbrillance du système au fur et à mesure de la progression de l’opération.

Un contrôle de barre de progression a une plage et une position actuelle. La plage représente la durée totale de l’opération et la position actuelle représente la progression de l’application vers la fin de l’opération. La procédure de fenêtre utilise la plage et la position actuelle pour déterminer le pourcentage de la barre de progression à remplir avec la couleur de surbrillance. Étant donné que les valeurs de la plage et de la position actuelle sont exprimées en tant qu’entiers signés, la plage possible des valeurs de position actuelles est comprise entre-2 147 483 648 et 2 147 483 647 inclus.

Pour plus d’informations sur l’utilisation de `CProgressCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="cprogressctrl"></a>CProgressCtrl :: CProgressCtrl

Construit un objet `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Notes

Après avoir construit l’objet `CProgressCtrl`, appelez `CProgressCtrl::Create` pour créer le contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>CProgressCtrl :: Create

Crée un contrôle de barre de progression et l’attache à un objet `CProgressCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de barre de progression. Appliquez une combinaison de stylesdescribed de fenêtre dans [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans la SDK Windows, en plus des styles de contrôle de barre de progression suivants, au contrôle :

- PBS_VERTICAL affiche les informations de progression verticalement, de haut en bas. Sans cet indicateur, le contrôle de barre de progression s’affiche horizontalement, de gauche à droite.

- PBS_SMOOTH affiche le remplissage graduel et lisse dans le contrôle de barre de progression. Sans cet indicateur, le contrôle se remplira avec des blocs.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle de barre de progression. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) . Étant donné que le contrôle doit être une fenêtre enfant, les coordonnées spécifiées sont relatives à la zone cliente du *pParentWnd*.

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de barre de progression, généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de barre de progression.

### <a name="return-value"></a>Valeur de retour

TRUE si l’objet `CProgressCtrl` est créé avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Vous construisez un objet `CProgressCtrl` en deux étapes. Tout d’abord, appelez le constructeur, qui crée l’objet `CProgressCtrl`, puis appelez `Create`, qui crée le contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>CProgressCtrl :: CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à l’objet `CProgressCtrl`.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de barre de progression. Appliquez n’importe quelle combinaison de styles de fenêtre décrite dans [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

*rectangulaire*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_** .

##  <a name="getbarcolor"></a>CProgressCtrl :: GetBarColor

Obtient la couleur de la barre de l’indicateur de progression pour le contrôle de barre de progression actuel.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valeur de retour

Couleur de la barre de progression actuelle, représentée sous la forme d’une valeur [COLORREF](/windows/win32/gdi/colorref) , ou CLR_DEFAULT si la couleur de la barre de l’indicateur de progression est la couleur par défaut.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) , qui est décrit dans le SDK Windows.

##  <a name="getbkcolor"></a>CProgressCtrl :: GetBkColor

Obtient la couleur d’arrière-plan de la barre de progression actuelle.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

Couleur d’arrière-plan de la barre de progression actuelle, représentée sous la forme d’une valeur [COLORREF](/windows/win32/gdi/colorref) .

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) , qui est décrit dans le SDK Windows.

##  <a name="getpos"></a>CProgressCtrl :: GetPos

Récupère la position actuelle de la barre de progression.

```
int GetPos();
```

### <a name="return-value"></a>Valeur de retour

Position du contrôle de barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais plutôt entre les plages supérieure et inférieure indiquées dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>CProgressCtrl :: GetRange

Obtient les limites inférieure et supérieure actuelles, ou la plage, du contrôle de barre de progression.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower*<br/>
Référence à un entier qui reçoit la limite inférieure du contrôle de barre de progression.

*nUpper*<br/>
Référence à un entier qui reçoit la limite supérieure du contrôle de barre de progression.

### <a name="remarks"></a>Notes

Cette fonction copie les valeurs des limites inférieure et supérieure des entiers référencés par *nLower* et *nUpper*, respectivement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>CProgressCtrl :: GetState

Obtient l’état du contrôle de barre de progression actuel.

```
int GetState() const;
```

### <a name="return-value"></a>Valeur de retour

État du contrôle de barre de progression actuel, qui est l’une des valeurs suivantes :

|Valeur|State|
|-----------|-----------|
|PBST_NORMAL|En cours|
|PBST_ERROR|Error|
|PBST_PAUSED|Suspendu|

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’état du contrôle de barre de progression actuel.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>CProgressCtrl :: GetStep

Récupère l’incrément de l’étape pour la barre de progression du contrôle de barre de progression actuel.

```
int GetStep() const;
```

### <a name="return-value"></a>Valeur de retour

Incrément de la barre de progression.

### <a name="remarks"></a>Notes

L’incrément d’étape correspond à la quantité par laquelle un appel à [CProgressCtrl :: StepIt](#stepit) augmente la position actuelle de la barre de progression.

Cette méthode envoie le message [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’incrément d’étape du contrôle de barre de progression actuel.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>CProgressCtrl :: OffsetPos

Avance la position actuelle du contrôle de barre de progression par l’incrément spécifié par *nPos* et redessine la barre pour refléter la nouvelle position.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Montant d’avance de la position.

### <a name="return-value"></a>Valeur de retour

Position précédente du contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>CProgressCtrl :: SetBarColor

Définit la couleur de la barre de l’indicateur de progression dans le contrôle de barre de progression actuel.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*clrBar*|dans Valeur [COLORREF](/windows/win32/gdi/colorref) qui spécifie la nouvelle couleur de la barre de l’indicateur de progression. Spécifiez CLR_DEFAULT pour que la barre de progression utilise sa couleur par défaut.|

### <a name="return-value"></a>Valeur de retour

Couleur précédente de la barre de l’indicateur de progression, représentée sous la forme d’une valeur [COLORREF](/windows/win32/gdi/colorref) , ou CLR_DEFAULT si la couleur de la barre de l’indicateur de progression est la couleur par défaut.

### <a name="remarks"></a>Notes

La méthode `SetBarColor` définit la couleur de la barre de progression uniquement si un [thème](/windows/win32/Controls/visual-styles-overview) Windows Vista n’est pas appliqué.

Cette méthode envoie le message [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie la couleur de la barre de progression en rouge, vert, bleu ou par défaut.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>CProgressCtrl :: SetBkColor

Définit la couleur d’arrière-plan de la barre de progression.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Paramètres

*clrNew*<br/>
Valeur COLORREF qui spécifie la nouvelle couleur d’arrière-plan. Spécifiez la valeur de CLR_DEFAULT pour utiliser la couleur d’arrière-plan par défaut pour la barre de progression.

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) indiquant la couleur d’arrière-plan précédente, ou CLR_DEFAULT si la couleur d’arrière-plan est la couleur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>CProgressCtrl :: SetMarquee

Active ou désactive le mode texte défilant pour le contrôle de barre de progression actuel.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fMarqueeMode*|dans TRUE pour activer le mode texte défilant ou FALSe pour désactiver le mode texte défilant.|
|*Nintervalle*|dans Durée en millisecondes entre les mises à jour de l’animation de texte défilant.|

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne toujours TRUE.

### <a name="remarks"></a>Notes

Quand le mode texte défilant est activé, la barre de progression est animée et fait défiler comme un signe sur un texte défilant.

Cette méthode envoie le message [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant démarre et arrête l’animation de défilement du texte défilant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>CProgressCtrl :: SetPos

Définit la position actuelle du contrôle de barre de progression telle qu’elle est spécifiée par *nPos* et redessine la barre pour refléter la nouvelle position.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Nouvelle position du contrôle de barre de progression.

### <a name="return-value"></a>Valeur de retour

Position précédente du contrôle de barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais plutôt entre les plages supérieure et inférieure indiquées dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>CProgressCtrl :: SetRange

Définit les limites supérieure et inférieure de la plage du contrôle de barre de progression et redessine la barre pour refléter les nouvelles plages.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower*<br/>
Spécifie la limite inférieure de la plage (la valeur par défaut est zéro).

*nUpper*<br/>
Spécifie la limite supérieure de la plage (la valeur par défaut est 100).

### <a name="remarks"></a>Notes

La fonction membre `SetRange32` définit la plage de bits 32 pour le contrôle Progress.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>CProgressCtrl :: SetState

Définit l'état du contrôle de barre de progression actuel.

```
int SetState(int iState);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iState*|dans État permettant de définir la barre de progression. Utilisez l’une des valeurs suivantes :<br /><br /> -PBST_NORMAL-en cours<br />-PBST_ERROR-erreur<br />-PBST_PAUSED-suspendu|

### <a name="return-value"></a>Valeur de retour

État précédent du contrôle de barre de progression actuel.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L'exemple de code suivant attribue au contrôle de barre de progression actuel l'état En pause ou Suspendu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>CProgressCtrl :: SetStep

Spécifie l’incrément de l’étape pour un contrôle de barre de progression.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Paramètres

*nStep*<br/>
Nouvel incrément de l’étape.

### <a name="return-value"></a>Valeur de retour

Incrément de l’étape précédente.

### <a name="remarks"></a>Notes

L’incrément d’étape correspond à la quantité par laquelle un appel à `CProgressCtrl::StepIt` augmente la position actuelle de la barre de progression.

L’incrément d’étape par défaut est 10.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>CProgressCtrl :: StepIt

Avance la position actuelle d’un contrôle de barre de progression à l’aide de l’incrément de l’étape et redessine la barre pour refléter la nouvelle position.

```
int StepIt();
```

### <a name="return-value"></a>Valeur de retour

Position précédente du contrôle de barre de progression.

### <a name="remarks"></a>Notes

L’incrément d’étape est défini par la fonction membre `CProgressCtrl::SetStep`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
