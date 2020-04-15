---
title: CDateTimeCtrl, classe
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
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321911"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl, classe

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
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Ferme la date actuelle et le contrôle du cueilleur d’heure.|
|[CDateTimeCtrl::Créer](#create)|Crée le contrôle de la date et `CDateTimeCtrl` de l’heure et le fixe à l’objet.|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Récupère des informations sur le contrôle actuel du cueilleur de dates et d’heure.|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Retourne la taille idéale du contrôle du cueilleur de date et d’heure qui est nécessaire pour afficher la date ou l’heure actuelles.|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Récupère la couleur pour une partie donnée du calendrier du mois dans le contrôle de la date et de l’heure de cueilleur.|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Récupère l’objet `CMonthCalCtrl` associé au contrôle de la date et de l’heure du cueilleur.|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Récupère la police actuellement utilisée par le contrôle du calendrier du mois des enfants du contrôle des mois d’enfant du cueilleur de dates et d’heure.|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Obtient le style de la date actuelle et le contrôle de l’heure picker.|
|[CDateTimeCtrl::GetRange](#getrange)|Récupère les heures minimales et maximales autorisées actuelles pour un contrôle de la date et de l’heure du cueilleur.|
|[CDateTimeCtrl::GetTime](#gettime)|Récupère l’heure actuellement sélectionnée à partir d’un contrôle `SYSTEMTIME` de cueilleur de dates et d’heures et le met dans une structure spécifiée.|
|[CDateTimeCtrl::SetFormat](#setformat)|Définit l’affichage d’un contrôle de cueilleur de date et d’heure conformément à une chaîne de format donnée.|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Définit la couleur pour une partie donnée du calendrier du mois dans un contrôle de date et d’heure de cueilleur.|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Définit la police que le contrôle du calendrier du mois de l’enfant du contrôle du mois de l’enfant du cueilleur de dates et d’heure utilisera.|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Définit le style du contrôle actuel du cueilleur de dates et d’heure.|
|[CDateTimeCtrl::SetRange](#setrange)|Définit les heures minimales et maximales autorisées du système pour un contrôle de la date et de l’heure du cueilleur.|
|[CDateTimeCtrl::SetTime](#settime)|Définit l’heure dans un contrôle de cueilleur de date et d’heure.|

## <a name="remarks"></a>Notes

Le contrôle du cueilleur de dates et d’heure (contrôle DTP) fournit une interface simple pour échanger des informations sur les dates et l’heure avec un utilisateur. Cette interface contient des champs, chacun d’eux affiche une partie des informations de date et d’heure stockées dans le contrôle. L’utilisateur peut modifier les informations stockées dans le contrôle en modifiant le contenu de la chaîne dans un champ donné. L’utilisateur peut se déplacer d’un champ à l’autre à l’aide de la souris ou du clavier.

Vous pouvez personnaliser le contrôle de la date et de l’heure en appliquant une variété de styles à l’objet lorsque vous la créez. Voir [Date et Time Picker Control Styles](/windows/win32/Controls/date-and-time-picker-control-styles) dans le SDK Windows pour plus d’informations sur les styles spécifiques à la date et le contrôle du cueilleur de temps. Vous pouvez définir le format d’affichage du contrôle DTP en utilisant des styles de format. Ces styles de format sont décrits sous "Format Styles" dans le sujet Windows SDK [Date et Time Picker Control Styles](/windows/win32/Controls/date-and-time-picker-control-styles).

Le contrôle de la date et de l’heure utilise également des notifications et des rappels, qui sont décrits dans [l’utilisation de CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl

Construit un objet `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal

Ferme la date actuelle et le contrôle du cueilleur d’heure.

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Notes

Cette méthode envoie le [message DTM_CLOSEMONTHCAL,](/windows/win32/Controls/dtm-closemonthcal) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder de façon programmatique au contrôle du cueilleur de dates et d’heures. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant clôt le calendrier d’abandon pour le contrôle actuel du cueilleur de dates et d’heure.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::Créer

Crée le contrôle de la date et `CDateTimeCtrl` de l’heure et le fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie la combinaison des styles de contrôle de l’heure de date. Consultez [les styles de contrôle de date et d’heure](/windows/win32/Controls/date-and-time-picker-control-styles) dans le SDK Windows pour plus d’informations sur les styles de cueilleur de dates et d’heure.

*Rect*<br/>
Une référence à une structure [RECT,](/previous-versions/dd162897\(v=vs.85\)) qui est la position et la taille de la date et le contrôle du cueilleur d’heure.

*pParentWnd*<br/>
Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente de la date et le contrôle du cueilleur d’heure. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle du cueilleur de date et d’heure.

### <a name="return-value"></a>Valeur de retour

Nonzero si la création a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

##### <a name="to-create-a-date-and-time-picker-control"></a>Créer un contrôle de cueilleur de dates et d’heure

1. Appelez [CDateTimeCtrl](#cdatetimectrl) pour `CDateTimeCtrl` construire un objet.

1. Appelez cette fonction de membre, qui crée le contrôle de `CDateTimeCtrl` la date et de l’heure Windows et le fixe à l’objet.

Lorsque vous `Create`appelez, les contrôles communs sont parasécés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo

Récupère des informations sur le contrôle actuel du cueilleur de dates et d’heure.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pDateTimePickerInfo (en anglais seulement)*|[out] Un pointeur à une structure [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) qui reçoit une description de la date actuelle et le contrôle du cueilleur d’heure.<br /><br /> L’appelant est responsable de l’attribution de cette structure. Cependant, cette méthode initialise le membre *cbSize* de la structure.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message DTM_GETDATETIMEPICKERINFO,](/windows/win32/Controls/dtm-getdatetimepickerinfo) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder de façon programmatique au contrôle du cueilleur de dates et d’heures. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant indique s’il récupère avec succès des informations sur le contrôle actuel du cueilleur de dates et d’heure.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor

Récupère la couleur pour une partie donnée du calendrier du mois dans le contrôle de la date et de l’heure de cueilleur.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Paramètres

*iColor (iColor)*<br/>
Une valeur **int** spécifiant quelle zone de couleur du calendrier du mois à récupérer. Pour une liste de valeurs, voir le *paramètre iColor* pour [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente le réglage des couleurs pour la partie spécifiée du contrôle du calendrier du mois en cas de succès. La fonction renvoie -1 si elle n’est pas retenue.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl

Récupère l’objet `CMonthCalCtrl` associé au contrôle de la date et de l’heure du cueilleur.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CMonthCalCtrl,](../../mfc/reference/cmonthcalctrl-class.md) ou NULL si échoué ou si la fenêtre n’est pas visible.

### <a name="remarks"></a>Notes

Les commandes de la date et de l’heure du calendrier créent un contrôle du calendrier du mois pour enfants lorsque l’utilisateur clique sur la flèche de dépôt. Lorsque `CMonthCalCtrl` l’objet n’est plus nécessaire, il est détruit, de sorte que votre application ne doit pas compter sur le stockage de l’objet représentant le calendrier du mois de l’enfant du contrôle du cueilleur d’heure de date.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont

Obtient la police actuellement utilisée par le contrôle du calendrier du calendrier du contrôle du mois du cueilleur de dates et d’heure.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CFont,](../../mfc/reference/cfont-class.md) ou NULL si échoué.

### <a name="remarks"></a>Notes

L’objet `CFont` pointé par la valeur de retour est un objet temporaire et est détruit pendant le prochain temps de traitement au ralenti.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle

Obtient le style du contrôle du calendrier des mois d’abandon qui est associé à la date actuelle et le contrôle du cueilleur d’heure.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Le style du contrôle du calendrier des mois de baisse, qui est une combinaison bitwise (OU) de la date et l’heure des styles de contrôle de cueilleur. Pour plus d’informations, voir [Styles de contrôle du calendrier des mois](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Notes

Cette méthode envoie le [message DTM_GETMCSTYLE,](/windows/win32/Controls/dtm-getmcstyle) qui est décrit dans le SDK Windows.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::GetRange

Récupère les heures minimales et maximales autorisées actuelles pour un contrôle de la date et de l’heure du cueilleur.

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
Un pointeur vers un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou un objet `CDateTimeCtrl` [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant le temps le plus tôt autorisé dans l’objet.

*pMaxRange (en)*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet ou un `CDateTimeCtrl` objet contenant le dernier temps autorisé dans l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD contenant des drapeaux indiquant quelles plages sont définies. Si

`return value & GDTR_MAX` == 0

alors le deuxième paramètre est valide. De même, si

`return value & GDTR_MIN` == 0

puis le premier paramètre est valide.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange), tel que décrit dans le SDK Windows. Dans la mise en œuvre `COleDateTime` `CTime` de MFC, vous pouvez spécifier soit ou utiliser.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl::GetTime

Récupère l’heure actuellement sélectionnée à partir d’un contrôle `SYSTEMTIME` de cueilleur de dates et d’heures et le met dans une structure spécifiée.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Paramètres

*timeDest*<br/>
Dans la première version, une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations de temps du système. Dans la deuxième version, une référence à un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations de temps du système.

*pTimeDest*<br/>
Un pointeur à la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations de temps du système. Ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Dans la première version, nonzero si le `COleDateTime` temps est écrit avec succès à l’objet; sinon 0. Dans les deuxième et troisième versions, une valeur DWORD égale au membre *dwFlag* défini dans la structure [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) Voir la section **Remarques** ci-dessous pour plus d’informations.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime), tel que décrit dans le SDK Windows. Dans la mise `GetTime`en œuvre `CTime` MFC de , `SYSTEMTIME` vous pouvez utiliser `COleDateTime` ou des classes, ou vous pouvez utiliser une structure, pour stocker les informations de temps.

La valeur de retour DWORD dans les deuxième et troisième versions, ci-dessus, indique si oui ou non la date et le contrôle du cueilleur d’heure est fixé à l’état «sans date», comme indiqué dans la structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) membre *dwFlags*. Si la valeur retournée équivaut à GDT_NONE, le contrôle est réglé à "pas de date" statut, et utilise le style DTS_SHOWNONE. Si la valeur retournée équivaut à GDT_VALID, le temps du système est stocké avec succès dans l’emplacement de destination.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize

Retourne la taille idéale du contrôle du cueilleur de date et d’heure qui est nécessaire pour afficher la date ou l’heure actuelles.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Psize*|[out] Pointeur vers une structure [SIZE](/windows/win32/api/windef/ns-windef-size) qui contient la taille idéale pour le contrôle.|

### <a name="return-value"></a>Valeur de retour

La valeur de retour est toujours VRAI.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message DTM_GETIDEALSIZE,](/windows/win32/Controls/dtm-getidealsize) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder de façon programmatique au contrôle du cueilleur de dates et d’heures. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère la taille idéale pour afficher le contrôle de la date et de l’heure du cueilleur.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::SetFormat

Définit l’affichage d’un contrôle de cueilleur de date et d’heure conformément à une chaîne de format donnée.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Paramètres

*pstrFormat (en)*<br/>
Un pointeur vers une chaîne de format à durée zéro qui définit l’écran désiré. La configuration de ce paramètre à NULL réinitialisera le contrôle à la chaîne de format par défaut pour le style actuel.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

> [!NOTE]
> L’entrée de l’utilisateur ne détermine pas le succès ou l’échec de cet appel.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor

Définit la couleur pour une partie donnée du calendrier du mois dans un contrôle de date et d’heure de cueilleur.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*iColor (iColor)*<br/>
la valeur **int** spécifiant quelle zone du contrôle du calendrier du mois à définir. Cette valeur peut être l’une des suivantes.

|Value|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|Définissez la couleur de fond affichée entre les mois.|
|MCSC_MONTHBK|Définissez la couleur de fond affichée dans un mois.|
|MCSC_TEXT|Définissez la couleur utilisée pour afficher le texte dans un délai d’un mois.|
|MCSC_TITLEBK|Définissez la couleur de fond affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|Définissez la couleur utilisée pour afficher le texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|Réglez la couleur utilisée pour afficher l’en-tête et le texte du jour de fuite. Les jours d’en-tête et les jours de fuite sont les jours des mois précédents et suivants qui apparaissent sur le calendrier actuel.|

*ref*<br/>
Une valeur COLORREF représentant la couleur qui sera définie pour la zone spécifiée du calendrier du mois.

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente le réglage de couleur précédent pour la partie spécifiée du contrôle du calendrier du mois en cas de succès. Sinon, le message renvoie -1.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont

Définit la police que le contrôle du calendrier du mois de l’enfant du contrôle du mois de l’enfant du cueilleur de dates et d’heure utilisera.

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Gérer la police qui sera réglée.

*bRedraw (en)*<br/>
Précise si le contrôle doit être redessiné immédiatement après la mise en place de la police. La définition de ce paramètre à TRUE provoque le redessiner le contrôle.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Si vous utilisez ce code, vous voudrez faire `CDialog`un membre de votre classe `CFont`dérivée appelé *m_MonthFont* de type .

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle

Définit le style du contrôle du calendrier des mois d’abandon qui est associé au contrôle actuel du cueilleur de dates et d’heure.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwStyle (en)*|[dans] Un nouveau style de contrôle de calendrier de calendrier, qui est une combinaison bitwise (OU) des modèles de contrôle de calendrier de mois. Pour plus d’informations, voir [Styles de contrôle du calendrier des mois](/windows/win32/Controls/month-calendar-control-styles).|

### <a name="return-value"></a>Valeur de retour

Le style précédent du contrôle du calendrier des mois d’abandon.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message DTM_SETMCSTYLE,](/windows/win32/Controls/dtm-setmcstyle) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder de façon programmatique au contrôle du cueilleur de dates et d’heures. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle de la date et de l’heure pour afficher les numéros de semaine, les noms abrégés des jours de la semaine, et aucun indicateur aujourd’hui.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::SetRange

Définit les heures minimales et maximales autorisées du système pour un contrôle de la date et de l’heure du cueilleur.

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
Un pointeur vers un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou un objet `CDateTimeCtrl` [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant le temps le plus tôt autorisé dans l’objet.

*pMaxRange (en)*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet ou un `CDateTimeCtrl` objet contenant le dernier temps autorisé dans l’objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange), tel que décrit dans le SDK Windows. Dans la mise en œuvre `COleDateTime` `CTime` de MFC, vous pouvez spécifier soit ou utiliser. Si `COleDateTime` l’objet a un statut NULL, la plage sera supprimée. Si `CTime` le pointeur ou le `COleDateTime` pointeur est NULL, la plage sera supprimée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CDateTimeCtrl:GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::SetTime

Définit l’heure dans un contrôle de cueilleur de date et d’heure.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Paramètres

*timeNew*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant le contrôle auquel le contrôle sera réglé.

*pTimeNew*<br/>
Dans la deuxième version ci-dessus, un pointeur vers un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant l’heure à laquelle le contrôle sera réglé. Dans la troisième version ci-dessus, un pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant l’heure à laquelle le contrôle sera réglé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime), tel que décrit dans le SDK Windows. Dans la mise `SetTime`en œuvre `COleDateTime` `CTime` MFC de , `SYSTEMTIME` vous pouvez utiliser le ou les classes, ou vous pouvez utiliser une structure, pour définir les informations de temps.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)
