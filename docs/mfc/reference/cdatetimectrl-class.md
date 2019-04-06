---
title: CDateTimeCtrl (classe)
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: 8c69473ab813c2fa692044fddc406a74a5aeb197
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779818"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl (classe)

Encapsule les fonctionnalités d'un contrôle de sélecteur de date et d'heure.

## <a name="syntax"></a>Syntaxe

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Construit un objet `CDateTimeCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Ferme le contrôle de sélecteur de date et l’heure actuels.|
|[CDateTimeCtrl::Create](#create)|Crée le contrôle de sélecteur de date et d’heure et l’attache à la `CDateTimeCtrl` objet.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Récupère des informations sur le contrôle de sélecteur de date et l’heure actuelle.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Retourne la taille idéale du contrôle de sélecteur de date et d’heure qui est nécessaire pour afficher la date actuelle ou l’heure.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Récupère la couleur pour une partie donnée du calendrier du mois dans le contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Récupère le `CMonthCalCtrl` objet associé avec le contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Récupère la police actuellement utilisée par la date et de contrôle de calendrier mensuel enfant du contrôle de sélecteur d’heure.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Obtient le style du contrôle de sélecteur de date et l’heure actuels.|
|[CDateTimeCtrl::GetRange](#getrange)|Récupère actuel minimale et maximale autorisées heures système pour un contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl::GetTime](#gettime)|Récupère l’heure actuellement sélectionnée à partir d’un contrôle de sélecteur de date et l’heure et le place dans une certaine `SYSTEMTIME` structure.|
|[CDateTimeCtrl::SetFormat](#setformat)|Définit l’affichage d’un contrôle de sélecteur de date et d’heure conformément à une chaîne de format donné.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Définit la couleur d’une partie donnée du calendrier du mois au sein d’un contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Définit la police qui contrôle month calendar de la date et l’heure sélecteur du contrôle enfant utilisera.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Définit le style du contrôle de sélecteur de date et l’heure actuels.|
|[CDateTimeCtrl::SetRange](#setrange)|Définit les heures système autorisée minimale et maximale pour un contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl::SetTime](#settime)|Définit l’heure dans un contrôle de sélecteur de date et d’heure.|

## <a name="remarks"></a>Notes

Le contrôle de sélecteur de date et d’heure (contrôle DTP) fournit une interface simple pour échanger des informations de date et d’heure avec un utilisateur. Cette interface contient des champs, chacun d’eux affiche une partie des informations de date et d’heure stockées dans le contrôle. L’utilisateur peut modifier les informations stockées dans le contrôle en modifiant le contenu de la chaîne dans un champ donné. L’utilisateur peut déplacer d’un champ à l’aide de la souris ou le clavier.

Vous pouvez personnaliser le contrôle de sélecteur de date et d’heure en appliquant des styles à l’objet lors de sa création. Consultez [Styles de Date et heure sélecteur contrôle](/windows/desktop/Controls/date-and-time-picker-control-styles) dans le SDK Windows pour plus d’informations sur les styles spécifiques pour le contrôle de sélecteur de date et d’heure. Vous pouvez définir le format d’affichage du contrôle DTP à l’aide de styles de formats. Ces styles de formats sont décrits sous « Format Styles » dans la rubrique du Kit de développement logiciel Windows [Styles de Date et heure sélecteur contrôle](/windows/desktop/Controls/date-and-time-picker-control-styles).

Le contrôle de sélecteur de date et d’heure utilise également des notifications et les rappels, qui sont décrites dans [à l’aide de CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

Construit un objet `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

Ferme le contrôle de sélecteur de date et l’heure actuels.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Notes

Cette méthode envoie le [DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisé pour accéder par programmation le contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant ferme le calendrier déroulant pour le contrôle de sélecteur de date et l’heure actuels.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

Crée le contrôle de sélecteur de date et d’heure et l’attache à la `CDateTimeCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie la combinaison de styles de contrôle de temps de date. Consultez [Styles de Date et heure sélecteur contrôle](/windows/desktop/Controls/date-and-time-picker-control-styles) dans le SDK Windows pour plus d’informations sur les styles de sélecteur de date et d’heure.

*rect*<br/>
Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure, qui est la position et la taille du contrôle de sélecteur de date et d’heure.

*pParentWnd*<br/>
Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle de sélecteur de date et d’heure. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle de. date et heure sélecteur du contrôle

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la création a réussi ; sinon 0.

### <a name="remarks"></a>Notes

##### <a name="to-create-a-date-and-time-picker-control"></a>Pour créer un contrôle de sélecteur de date et d’heure

1. Appelez [CDateTimeCtrl](#cdatetimectrl) pour construire un `CDateTimeCtrl` objet.

1. Appelez cette fonction membre, ce qui crée le contrôle de sélecteur de date et l’heure de Windows et l’attache à la `CDateTimeCtrl` objet.

Lorsque vous appelez `Create`, les contrôles communs sont initialisés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

Récupère des informations sur le contrôle de sélecteur de date et l’heure actuelle.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out] Un pointeur vers un [DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo) structure qui reçoit une description du contrôle de sélecteur de date et l’heure actuelle.<br /><br /> L’appelant est chargé d’allouer cette structure. Toutefois, cette méthode initialise la *cbSize* membre de la structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisé pour accéder par programmation le contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant indique si elle a réussi à récupérer d’informations sur le contrôle de sélecteur de date et l’heure actuelle.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

Récupère la couleur pour une partie donnée du calendrier du mois dans le contrôle de sélecteur de date et d’heure.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Paramètres

*iColor*<br/>
Un **int** valeur qui spécifie la zone de couleur du calendrier du mois à récupérer. Pour obtenir la liste de valeurs, consultez le *iColor* paramètre pour [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valeur de retour

Valeur COLORREF qui représente le paramètre de couleur pour la partie spécifiée du contrôle month calendar en cas de réussite. La fonction retourne -1 en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl

Récupère le `CMonthCalCtrl` objet associé avec le contrôle de sélecteur de date et d’heure.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) de l’objet, ou NULL en cas d’échec ou si la fenêtre n’est pas visible.

### <a name="remarks"></a>Notes

Contrôles de sélecteur de date et heure de créent un contrôle enfant month calendar lorsque l’utilisateur clique sur la flèche déroulante. Lorsque le `CMonthCalCtrl` objet n’est plus nécessaire, il est détruit, donc votre application ne doit pas s’appuyer sur le stockage de l’objet qui représente le calendrier du mois du contrôle date time picker enfant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

Obtient la police actuellement utilisée par la date et de contrôle de calendrier mensuel du contrôle de sélecteur d’heure.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [CFont](../../mfc/reference/cfont-class.md) de l’objet, ou NULL en cas d’échec.

### <a name="remarks"></a>Notes

Le `CFont` objet désigné par la valeur de retour est un objet temporaire et est détruit pendant la durée de traitement d’inactivité suivante.

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

Obtient le style du contrôle calendar month de la liste déroulante qui est associé avec le contrôle de sélecteur de date et l’heure actuels.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Le style du contrôle de calendrier mois de la liste déroulante, qui est une combinaison au niveau du bit (ou) de styles de contrôle de sélecteur de date et d’heure. Pour plus d’informations, consultez [Styles de contrôle Month Calendar](/windows/desktop/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Notes

Cette méthode envoie le [DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle) message, qui est décrite dans le SDK Windows.

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

Récupère actuel minimale et maximale autorisées heures système pour un contrôle de sélecteur de date et d’heure.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>Paramètres

*pMinRange*<br/>
Un pointeur vers un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet ou un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la première heure autorisée dans le `CDateTimeCtrl` objet.

*pMaxRange*<br/>
Un pointeur vers un `COleDateTime` objet ou un `CTime` objet contenant la dernière heure autorisée dans le `CDateTimeCtrl` objet.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui contient les indicateurs qui indiquent les plages sont définies. If

`return value & GDTR_MAX` == 0

puis le deuxième paramètre est valid. De même, si

`return value & GDTR_MIN` == 0

le premier paramètre est valid.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC, vous pouvez spécifier soit `COleDateTime` ou `CTime` utilisations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

Récupère l’heure actuellement sélectionnée à partir d’un contrôle de sélecteur de date et l’heure et le place dans une certaine `SYSTEMTIME` structure.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Paramètres

*timeDest*<br/>
Dans la première version, une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui recevra les informations d’heure système. Dans la deuxième version, une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui recevra les informations d’heure système.

*pTimeDest*<br/>
Un pointeur vers le [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) structure qui doit recevoir les informations d’heure système. Ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Dans la première version, différent de zéro si l’heure est correctement écrite dans le `COleDateTime` objet ; sinon 0. Dans les versions des deuxième et troisième, une valeur DWORD de valeur égale à la *dwFlag* membre défini le [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) structure. Consultez le **notes** section ci-dessous pour plus d’informations.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetTime`, vous pouvez utiliser `COleDateTime` ou `CTime` classes, ou vous pouvez utiliser un `SYSTEMTIME` structure pour stocker les informations d’heure.

La valeur de retour DWORD dans les versions des deuxième et troisième, ci-dessus, indique si le contrôle de sélecteur de date et l’heure est défini sur l’état « aucune date », comme indiqué dans le [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) membre de structure *dwFlags* . Si la valeur retournée est égale à GDT_NONE, le contrôle a la valeur de l’état de « aucune date » et utilise le style DTS_SHOWNONE. Si la valeur retournée est égale à GDT_VALID, l’heure système est correctement stockée dans l’emplacement de destination.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

Retourne la taille idéale du contrôle de sélecteur de date et d’heure qui est nécessaire pour afficher la date actuelle ou l’heure.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*psize*|[out] Pointeur vers un [taille](/windows/desktop/api/windef/ns-windef-tagsize) structure qui contient la taille idéale pour le contrôle.|

### <a name="return-value"></a>Valeur de retour

La valeur de retour est toujours TRUE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisé pour accéder par programmation le contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère la taille idéale pour afficher le contrôle de sélecteur de date et d’heure.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

Définit l’affichage d’un contrôle de sélecteur de date et d’heure conformément à une chaîne de format donné.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Paramètres

*pstrFormat*<br/>
Un pointeur vers une chaîne de format se terminant par zéro qui définit l’affichage de votre choix. Ce paramètre avec la valeur NULL réinitialisera le contrôle à la chaîne de format par défaut pour le style actuel.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

> [!NOTE]
>  L’entrée d’utilisateur ne détermine pas la réussite ou l’échec pour cet appel.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

Définit la couleur d’une partie donnée du calendrier du mois au sein d’un contrôle de sélecteur de date et d’heure.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*iColor*<br/>
**int** valeur qui spécifie la zone de contrôle month calendar à définir. Cette valeur peut être une des opérations suivantes.

|Value|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|Définissez la couleur d’arrière-plan affichée entre les mois.|
|MCSC_MONTHBK|Définir la couleur d’arrière-plan affichée dans un mois.|
|MCSC_TEXT|Définir la couleur utilisée pour afficher le texte au sein d’un mois.|
|MCSC_TITLEBK|Définir la couleur d’arrière-plan affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|Définir la couleur utilisée pour afficher du texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|Définissez la couleur utilisée pour afficher l’en-tête et le texte des jours de fin. Les jours précédents et sont les jours des mois précédents et suivants qui s’affichent sur le calendrier actuel.|

*ref*<br/>
Valeur COLORREF qui représente la couleur qui sera définie pour la zone spécifiée du calendrier du mois.

### <a name="return-value"></a>Valeur de retour

Valeur COLORREF qui représente le paramètre de couleur précédente pour la partie spécifiée du contrôle month calendar en cas de réussite. Sinon, le message retourne -1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

Définit la police qui contrôle month calendar de la date et l’heure sélecteur du contrôle enfant utilisera.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Handle de la police qui sera définie.

*bRedraw*<br/>
Spécifie si le contrôle doit être redessiné immédiatement lors de la définition de la police. Ce paramètre sur TRUE, le contrôle à redessiner.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  Si vous utilisez ce code, vous souhaiterez faire un membre de votre `CDialog`-classe appelée dérivée *m_MonthFont* de type `CFont`.

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

Définit le style du contrôle calendar month de la liste déroulante qui est associé avec le contrôle de sélecteur de date et l’heure actuels.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwStyle*|[in] Un nouveau mois calendrier style de contrôle, qui est une combinaison au niveau du bit (ou) de styles de contrôle month calendar. Pour plus d’informations, consultez [Styles de contrôle Month Calendar](/windows/desktop/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Valeur de retour

Le style précédent du contrôle calendar month de la liste déroulante.

### <a name="remarks"></a>Notes

Cette méthode envoie le [DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisé pour accéder par programmation le contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle de sélecteur de date et d’heure pour afficher les numéros de semaine, les noms abrégés des jours de la semaine et aucun indicateur aujourd'hui.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

Définit les heures système autorisée minimale et maximale pour un contrôle de sélecteur de date et d’heure.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>Paramètres

*pMinRange*<br/>
Un pointeur vers un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet ou un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la première heure autorisée dans le `CDateTimeCtrl` objet.

*pMaxRange*<br/>
Un pointeur vers un `COleDateTime` objet ou un `CTime` objet contenant la dernière heure autorisée dans le `CDateTimeCtrl` objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC, vous pouvez spécifier soit `COleDateTime` ou `CTime` utilisations. Si le `COleDateTime` objet a un état NULL, la plage est supprimée. Si le `CTime` pointeur ou le `COleDateTime` pointeur est NULL, la plage est supprimée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CDateTimeCtrl::GetRange](#getrange).

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

Définit l’heure dans un contrôle de sélecteur de date et d’heure.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Paramètres

*timeNew*<br/>
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet contenant l’à laquelle le contrôle est défini.

*pTimeNew*<br/>
Dans la deuxième version ci-dessus, un pointeur vers un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant l’heure défini pour le contrôle. Dans la troisième version ci-dessus, un pointeur vers un [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) structure contenant l’heure défini pour le contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetTime`, vous pouvez utiliser la `COleDateTime` ou `CTime` classes, ou vous pouvez utiliser un `SYSTEMTIME` structure, pour définir les informations d’heure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl (classe)](../../mfc/reference/cmonthcalctrl-class.md)
