---
title: CProgressCtrl (classe)
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
ms.openlocfilehash: 15241485278f09d16c86fc7274f2fc1d85a7a2f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778947"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (classe)

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
|[CProgressCtrl::Create](#create)|Crée un contrôle de barre de progression et l’attache à un `CProgressCtrl` objet.|
|[CProgressCtrl::CreateEx](#createex)|Crée un contrôle de progression avec les styles étendus Windows spécifiés et l’attache à un `CProgressCtrl` objet.|
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtient la couleur de la barre de progression pour le contrôle de barre de progression actuel.|
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtient la couleur d’arrière-plan de la barre de progression actuel.|
|[CProgressCtrl::GetPos](#getpos)|Obtient la position actuelle de la barre de progression.|
|[CProgressCtrl::GetRange](#getrange)|Obtient les limites inférieures et supérieures de la plage du contrôle de barre de progression.|
|[CProgressCtrl::GetState](#getstate)|Obtient l’état du contrôle de barre de progression actuel.|
|[CProgressCtrl::GetStep](#getstep)|Récupère l’incrément de l’étape de la barre de progression du contrôle de barre de progression actuel.|
|[CProgressCtrl::OffsetPos](#offsetpos)|Avance la position actuelle d’un contrôle de barre de progression d’un incrément spécifié, puis le redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl::SetBarColor](#setbarcolor)|Définit la couleur de la barre de progression dans le contrôle de barre de progression actuel.|
|[CProgressCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan de la barre de progression.|
|[CProgressCtrl::SetMarquee](#setmarquee)|Désactive le mode texte défilant activé ou désactivé pour le contrôle de barre de progression actuel.|
|[CProgressCtrl::SetPos](#setpos)|Définit la position actuelle pour un contrôle de barre de progression et redessine la barre pour refléter la nouvelle position.|
|[CProgressCtrl::SetRange](#setrange)|Définit les plages minimales et maximales pour un contrôle de barre de progression et redessine la barre pour refléter les nouvelles plages.|
|[CProgressCtrl::SetState](#setstate)|Définit l'état du contrôle de barre de progression actuel.|
|[CProgressCtrl::SetStep](#setstep)|Spécifie l’incrément de l’étape pour un contrôle de barre de progression.|
|[CProgressCtrl::StepIt](#stepit)|Avance la position actuelle pour un contrôle de barre de progression de l’incrément de l’étape (consultez [SetStep](#setstep)), puis le redessine la barre pour refléter la nouvelle position.|

## <a name="remarks"></a>Notes

Un contrôle de barre de progression est une fenêtre qu’une application peut utiliser pour indiquer la progression d’une opération longue. Il se compose d’un rectangle qui se remplit progressivement, de gauche à droite, avec le système de couleur de surbrillance qu’une opération progresse.

Un contrôle de barre de progression a une plage et une position actuelle. La plage représente la durée totale de l’opération, et la position actuelle représente la progression de que l’application a effectué l’opération. La procédure de fenêtre utilise la plage et la position actuelle pour déterminer le pourcentage de la barre de progression à remplir avec la couleur de surbrillance. Étant donné que la plage et les valeurs de position actuelles sont exprimées sous forme d’entiers signés, la plage possible de valeurs de position actuelle provient allant de -2,147,483,648 à 2 147 483 647 inclus.

Pour plus d’informations sur l’utilisation de `CProgressCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CProgressCtrl](../../mfc/using-cprogressctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl

Construit un objet `CProgressCtrl`.

```
CProgressCtrl();
```

### <a name="remarks"></a>Notes

Après avoir construit le `CProgressCtrl` de l’objet, appelez `CProgressCtrl::Create` pour créer le contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>  CProgressCtrl::Create

Crée un contrôle de barre de progression et l’attache à un `CProgressCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de barre de progression. Appliquer n’importe quelle combinaison de stylesdescribed de fenêtre dans [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) dans le SDK Windows, en plus de la barre des styles de contrôle, au contrôle de progression suivante :

- PBS_VERTICAL affiche verticalement les informations de progression, de haut en bas. Sans cet indicateur, le contrôle de barre de progression s’affiche horizontalement, de gauche à droite.

- Progressif de PBS_SMOOTH affiche smooth remplissage dans le contrôle de barre de progression. Sans cet indicateur, le contrôle se remplira avec des blocs.

*rect*<br/>
Spécifie la taille et la position du contrôle de barre de progression. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure. Étant donné que le contrôle doit être une fenêtre enfant, les coordonnées spécifiées sont par rapport à la zone cliente de la *pParentWnd*.

*pParentWnd*<br/>
Spécifie la barre fenêtre parent du contrôle de progression généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de barre de progression

### <a name="return-value"></a>Valeur de retour

TRUE si le `CProgressCtrl` objet est créé avec succès ; sinon, FALSE.

### <a name="remarks"></a>Notes

Vous construisez un `CProgressCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, ce qui crée le `CProgressCtrl` de l’objet, puis appelez `Create`, ce qui crée le contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>  CProgressCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe le `CProgressCtrl` objet.

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
Spécifie le style du contrôle de barre de progression. Appliquer n’importe quelle combinaison de styles de fenêtre décrit dans [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) dans le SDK Windows.

*rect*<br/>
Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor

Obtient la couleur de la barre de progression pour le contrôle de barre de progression actuel.

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de la barre de progression actuel, représenté sous la forme un [COLORREF](/windows/desktop/gdi/colorref) valeur ou CLR_DEFAULT si la couleur de barre de progression indicateur est la couleur par défaut.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PBM_GETBARCOLOR](/windows/desktop/Controls/pbm-getbarcolor) message, qui est décrite dans le SDK Windows.

##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor

Obtient la couleur d’arrière-plan de la barre de progression actuel.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur d’arrière-plan de la barre de progression actuel, représenté sous la forme un [COLORREF](/windows/desktop/gdi/colorref) valeur.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PBM_GETBKCOLOR](/windows/desktop/Controls/pbm-getbkcolor) message, qui est décrite dans le SDK Windows.

##  <a name="getpos"></a>  CProgressCtrl::GetPos

Récupère la position actuelle de la barre de progression.

```
int GetPos();
```

### <a name="return-value"></a>Valeur de retour

La position du contrôle de barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais au lieu de cela est entre le coin supérieur et inférieur plage indiquée dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>  CProgressCtrl::GetRange

Obtient les limites inférieures et supérieures actuelles, ou plage, du contrôle de barre de progression.

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower*<br/>
Une référence à un entier de réception de la limite inférieure du contrôle de barre de progression.

*nUpper*<br/>
Une référence à un entier de réception de la limite supérieure du contrôle de barre de progression.

### <a name="remarks"></a>Notes

Cette fonction copie les valeurs des limites inférieures et supérieures pour les entiers référencés par *nLower* et *nUpper*, respectivement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>  CProgressCtrl::GetState

Obtient l’état du contrôle de barre de progression actuel.

```
int GetState() const;
```

### <a name="return-value"></a>Valeur de retour

L’état du contrôle de barre de progression actuel, qui est une des valeurs suivantes :

|Value|État|
|-----------|-----------|
|PBST_NORMAL|En cours|
|PBST_ERROR|Error|
|PBST_PAUSED|Suspendu|

### <a name="remarks"></a>Notes

Cette méthode envoie le [PBM_GETSTATE](/windows/desktop/Controls/pbm-getstate) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’état du contrôle de barre de progression actuel.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>  CProgressCtrl::GetStep

Récupère l’incrément de l’étape de la barre de progression du contrôle de barre de progression actuel.

```
int GetStep() const;
```

### <a name="return-value"></a>Valeur de retour

L’incrément de l’étape de la barre de progression.

### <a name="remarks"></a>Notes

L’incrément de l’étape est le montant par lequel un appel à [CProgressCtrl::StepIt](#stepit) augmente la position actuelle de la barre de progression.

Cette méthode envoie le [PBM_GETSTEP](/windows/desktop/Controls/pbm-getstep) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère l’incrément de l’étape du contrôle de barre de progression actuel.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos

Avance la barre la position actuelle du contrôle de progression de l’incrément spécifié par *nPos* et redessine la barre pour refléter la nouvelle position.

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Montant à l’avance la position.

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de barre de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor

Définit la couleur de la barre de progression dans le contrôle de barre de progression actuel.

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*clrBar*|[in] Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui spécifie la nouvelle couleur de la barre de progression. Spécifiez CLR_DEFAULT pour provoquer la barre de progression à utiliser sa couleur par défaut.|

### <a name="return-value"></a>Valeur de retour

La couleur précédente de la barre de progression, représenté sous la forme un [COLORREF](/windows/desktop/gdi/colorref) valeur ou CLR_DEFAULT si la couleur de la barre de progression est la couleur par défaut.

### <a name="remarks"></a>Notes

Le `SetBarColor` méthode définit la progression de la barre uniquement si de couleur un Vista Windows [thème](/windows/desktop/Controls/visual-styles-overview) n’est pas en vigueur.

Cette méthode envoie le [PBM_SETBARCOLOR](/windows/desktop/Controls/pbm-setbarcolor) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant modifie la couleur de la barre de progression pour le rouge, vert, bleu ou la valeur par défaut.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor

Définit la couleur d’arrière-plan de la barre de progression.

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>Paramètres

*clrNew*<br/>
Valeur COLORREF qui spécifie la nouvelle couleur d’arrière-plan. Spécifiez la valeur CLR_DEFAULT pour utiliser la couleur d’arrière-plan par défaut pour la barre de progression.

### <a name="return-value"></a>Valeur de retour

Le [COLORREF](/windows/desktop/gdi/colorref) valeur qui indique la couleur d’arrière-plan précédente, ou CLR_DEFAULT si la couleur d’arrière-plan est la couleur par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee

Désactive le mode texte défilant activé ou désactivé pour le contrôle de barre de progression actuel.

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*fMarqueeMode*|[in] True pour activer le mode de texte défilant on, ou FALSE pour désactiver le mode de sélection.|
|*nInterval*|[in] Durée en millisecondes entre les mises à jour de l’animation de texte défilant.|

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Lorsque le mode de sélection est activé, la barre de progression est animée et fait défiler comme une connexion sur un texte défilant de théâtre.

Cette méthode envoie le [PBM_SETMARQUEE](/windows/desktop/Controls/pbm-setmarquee) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant démarre et arrête l’animation défilant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>  CProgressCtrl::SetPos

Définit la progression de la barre position actuelle du contrôle tel que spécifié par *nPos* et redessine la barre pour refléter la nouvelle position.

```
int SetPos(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Nouvelle position du contrôle de barre de progression.

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de barre de progression.

### <a name="remarks"></a>Notes

La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais au lieu de cela est entre le coin supérieur et inférieur plage indiquée dans [SetRange](#setrange).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>  CProgressCtrl::SetRange

Définit les limites supérieures et inférieures de la barre de plage du contrôle de progression et redessine la barre pour refléter les nouvelles plages.

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
Spécifie la limite inférieure de la plage (valeur par défaut est zéro).

*nUpper*<br/>
Spécifie la limite supérieure de la plage (valeur par défaut est 100).

### <a name="remarks"></a>Notes

La fonction membre `SetRange32` définit la plage de 32 bits pour le contrôle de progression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>  CProgressCtrl::SetState

Définit l'état du contrôle de barre de progression actuel.

```
int SetState(int iState);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iState*|[in] L’état à définir la barre de progression. Utilisez l'une des valeurs suivantes :<br /><br /> -PBST_NORMAL - en cours<br />-PBST_ERROR - erreur<br />-PBST_PAUSED - suspendu|

### <a name="return-value"></a>Valeur de retour

État précédent du contrôle de barre de progression actuel.

### <a name="remarks"></a>Notes

Cette méthode envoie le [PBM_SETSTATE](/windows/desktop/Controls/pbm-setstate) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>Exemple

L'exemple de code suivant attribue au contrôle de barre de progression actuel l'état En pause ou Suspendu.

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>  CProgressCtrl::SetStep

Spécifie l’incrément de l’étape pour un contrôle de barre de progression.

```
int SetStep(int nStep);
```

### <a name="parameters"></a>Paramètres

*nStep*<br/>
Nouvel incrément de l’étape.

### <a name="return-value"></a>Valeur de retour

L’incrément étape précédente.

### <a name="remarks"></a>Notes

L’incrément de l’étape est le montant par lequel un appel à `CProgressCtrl::StepIt` augmente la progression de la barre de la position actuelle.

L’incrément d’étape par défaut est 10.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>  CProgressCtrl::StepIt

Avance la position actuelle pour un contrôle de barre de progression de l’incrément de l’étape et redessine la barre pour refléter la nouvelle position.

```
int StepIt();
```

### <a name="return-value"></a>Valeur de retour

La position précédente du contrôle de barre de progression.

### <a name="remarks"></a>Notes

L’incrément de l’étape est définie par le `CProgressCtrl::SetStep` fonction membre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
