---
title: Classe CMonthCalCtrl
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: da9d588811361d3dfd72d44d5b9ced8460d23936
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319754"
---
# <a name="cmonthcalctrl-class"></a>Classe CMonthCalCtrl

Encapsule les fonctionnalités d'un contrôle Month Calendar.

## <a name="syntax"></a>Syntaxe

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Construit un objet `CMonthCalCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMonthCalCtrl::Créer](#create)|Crée un contrôle de calendrier d’un mois et l’attache à l’objet. `CMonthCalCtrl`|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Récupère la largeur de la bordure du contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Récupère le nombre de calendriers affichés dans le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Récupère des informations sur le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Récupère l’identifiant de calendrier pour le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetColor](#getcolor)|Obtient la couleur d’une zone spécifiée d’un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Récupère la vue qui est actuellement affichée par le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Récupère l’heure du système comme indiqué à la date actuellement sélectionnée.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtient le premier jour de la semaine pour être affiché dans la colonne la plus gauche du calendrier.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Récupère le nombre maximal actuel de jours qui peuvent être sélectionnés dans un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Récupère la largeur maximale de la chaîne "Aujourd’hui" pour le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Récupère la taille minimale requise pour afficher un mois complet dans un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Récupère le taux de défilement pour un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Récupère les informations de date représentant les limites élevées et basses de l’affichage d’un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetRange](#getrange)|Récupère les dates minimales et maximales actuelles fixées dans un contrôle de calendrier de mois.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Récupère les informations de date représentant les limites supérieures et inférieures de la plage de date actuellement sélectionnées par l’utilisateur.|
|[CMonthCalCtrl::GetToday](#gettoday)|Récupère les informations de date pour la date spécifiée comme "aujourd’hui" pour un contrôle de calendrier de mois.|
|[CMonthCalCtrl::HitTest](#hittest)|Détermine quelle section d’un contrôle de calendrier de mois se trouve à un point donné sur l’écran.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue du siècle.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue de la décennie.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue du mois.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue de l’année.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Définit la largeur de la bordure du contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Définit la largeur par défaut de la bordure du contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Définit l’identifiant du calendrier pour le contrôle du calendrier du mois en cours.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Définit le contrôle du calendrier du mois en cours pour afficher la vue du siècle.|
|[CMonthCalCtrl::SetColor](#setcolor)|Définit la couleur d’une zone spécifiée d’un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Définit le contrôle du calendrier du mois en cours pour afficher la vue spécifiée.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Définit la date actuellement sélectionnée pour un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Définit l’affichage pendant des jours dans un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Définit le contrôle du calendrier du mois en cours à la vue de la décennie.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Définit le nombre maximum de jours qui peuvent être sélectionnés dans un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Définit le taux de défilement pour un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Définit le contrôle du calendrier du mois en cours pour afficher la vue du mois.|
|[CMonthCalCtrl::SetRange](#setrange)|Définit les dates minimales et maximales autorisées pour un contrôle de calendrier de mois.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Définit la sélection pour un contrôle de calendrier d’un mois à une plage de date donnée.|
|[CMonthCalCtrl::SetToday](#settoday)|Définit le contrôle du calendrier pour le jour en cours.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Définit le contrôle du calendrier du mois en cours à la vue de l’année.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Repeinte le contrôle du calendrier du mois à sa taille minimale d’un mois.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Pour le contrôle du calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui s’adaptent dans un rectangle spécifié.|

## <a name="remarks"></a>Notes

Le contrôle de calendrier du mois fournit à l’utilisateur une interface de calendrier simple, à partir de laquelle l’utilisateur peut sélectionner une date. L’utilisateur peut modifier l’affichage en :

- Faire défiler vers l’arrière et vers l’avant, d’un mois à l’autre.

- Cliquez sur le texte Today pour afficher le jour en cours (si le style MCS_NOTODAY n’est pas utilisé).

- Choisir un mois ou un an à partir d’un menu pop-up.

Vous pouvez personnaliser le contrôle du calendrier du mois en appliquant une variété de styles à l’objet lorsque vous le créez. Ces styles sont décrits dans [les styles de contrôle de calendrier](/windows/win32/Controls/month-calendar-control-styles) de mois dans le SDK windows.

Le contrôle du calendrier du mois peut s’afficher plus d’un mois, et il peut indiquer des jours spéciaux (tels que les vacances) en antillant la date.

Pour plus d’informations sur l’utilisation du contrôle du calendrier des mois, voir [Utiliser CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl

Construit un objet `CMonthCalCtrl`.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Notes

Vous devez `Create` appeler après avoir construit l’objet.

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Créer

Crée un contrôle de calendrier d’un mois et l’attache à l’objet. `CMonthCalCtrl`

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie la combinaison de styles Windows appliqués au contrôle du calendrier du mois. Voir [les styles de contrôle du calendrier](/windows/win32/Controls/month-calendar-control-styles) des mois dans le SDK Windows pour plus d’informations sur les styles.

*Rect*<br/>
Une référence à une structure [RECT.](/previous-versions/dd162897\(v=vs.85\)) Contient la position et la taille du contrôle du calendrier du mois.

*Pt*<br/>
Une référence à une structure [POINT](/previous-versions/dd162805\(v=vs.85\)) qui identifie l’emplacement du contrôle du calendrier du mois.

*pParentWnd*<br/>
Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle du calendrier du mois. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle du calendrier du mois.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Créez un contrôle de calendrier d’un mois en deux étapes :

1. Appelez [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) pour `CMonthCalCtrl` construire un objet.

1. Appelez cette fonction de membre, qui crée un `CMonthCalCtrl` contrôle de calendrier de mois et l’attache à l’objet.

Lorsque vous `Create`appelez, les contrôles communs sont parasécés. La version `Create` de votre appel détermine la taille de sa taille :

- Pour que MFC taille automatiquement le contrôle à un mois, appelez le remplacement qui utilise le *paramètre pt.*

- Pour tailler le contrôle vous-même, appelez le remplacement de cette fonction qui utilise le *paramètre rect.*

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder

Récupère la largeur de la bordure du contrôle du calendrier du mois en cours.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la bordure de contrôle, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCALENDARBORDER,](/windows/win32/Controls/mcm-getcalendarborder) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount

Récupère le nombre de calendriers affichés dans le contrôle du calendrier du mois en cours.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de calendriers actuellement affichés dans le contrôle du calendrier du mois. Le nombre maximum autorisé de calendriers est de 12.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCALENDARCOUNT,](/windows/win32/Controls/mcm-getcalendarcount) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo

Récupère des informations sur le contrôle du calendrier du mois en cours.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pmcGridInfo*|[out] Pointeur vers une structure [MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) qui reçoit des informations sur le contrôle du calendrier du mois en cours. L’appelant est responsable de l’attribution et de l’initialisation de cette structure.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCALENDARGRIDINFO,](/windows/win32/Controls/mcm-getcalendargridinfo) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de `GetCalendarGridInfo` code suivant utilise la méthode pour récupérer la date de calendrier que le contrôle du calendrier du mois en cours affiche.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID

Récupère l’identifiant de calendrier pour le contrôle du calendrier du mois en cours.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Valeur de retour

Une des constantes [d’identification](/windows/win32/Intl/calendar-identifiers) de calendrier.

### <a name="remarks"></a>Notes

Un identificateur de calendrier désigne un calendrier spécifique à la région, comme les calendriers grégoriens (localisés), japonais ou Hijri. Votre application peut utiliser un identifiant de calendrier qui a différentes fonctions de support linguistique.

Cette méthode envoie le [message MCM_GETCALID,](/windows/win32/Controls/mcm-getcalid) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor

Récupère la couleur d’une zone du contrôle du calendrier du mois spécifiée par *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Paramètres

*nRégion*<br/>
La région du contrôle du calendrier du mois à partir de laquelle la couleur est récupérée. Pour une liste de valeurs, voir le *paramètre nRegion* de [SetColor](#setcolor).

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) spécifiant la couleur associée à la partie du contrôle du calendrier du mois, si elle est réussie. Sinon, cette fonction de membre renvoie -1.

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView

Récupère la vue qui est actuellement affichée par le contrôle du calendrier du mois en cours.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Valeur de retour

Le point de vue actuel, qui est indiqué par l’une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|MCMV_MONTH|Vue mensuelle|
|MCMV_YEAR|Vue annuelle|
|MCMV_DECADE|Vue de décennie|
|MCMV_CENTURY|Vue de siècle|

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant indique que le contrôle du calendrier du mois s’affiche actuellement.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel

Récupère l’heure du système comme indiqué à la date actuellement sélectionnée.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou à un objet [CTime.](../../atl-mfc-shared/reference/ctime-class.md) Reçoit l’heure actuelle.

*pDateTime (en)*<br/>
Un pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui recevra les informations de date actuellement sélectionnées. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; otherwize 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel), tel que décrit dans le SDK Windows.

> [!NOTE]
> Cette fonction de membre échoue si le style MCS_MULTISELECT est défini.

Dans la mise en `GetCurSel`œuvre `COleDateTime` de MFC, vous pouvez spécifier une utilisation, une `CTime` utilisation ou une `SYSTEMTIME` utilisation de la structure.

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek

Obtient le premier jour de la semaine pour être affiché dans la colonne la plus gauche du calendrier.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbLocal*<br/>
Un pointeur à une valeur BOOL. Si la valeur n’est pas nulle, le paramètre du contrôle ne correspond pas au paramètre du panneau de contrôle.

### <a name="return-value"></a>Valeur de retour

Une valeur integer qui représente le premier jour de la semaine. Voir **Remarques** pour plus d’informations sur ce que ces entiers représentent.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek), tel que décrit dans le SDK Windows. Les jours de la semaine sont représentés comme des intégraux, comme suit.

|Value|Jour de la semaine|
|-----------|---------------------|
|0|Lundi|
|1|Mardi|
|2|Mercredi|
|3|Jeudi|
|4|Vendredi|
|5|Samedi|
|6|Dimanche|

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMonthCalCtrl:SetFirstDayOfWeek](#setfirstdayofweek).

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount

Récupère le nombre maximal actuel de jours qui peuvent être sélectionnés dans un contrôle de calendrier de mois.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur integer qui représente le nombre total de jours qui peuvent être sélectionnés pour le contrôle.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount), tel que décrit dans le SDK Windows. Utilisez cette fonction de membre pour les contrôles avec l’ensemble de style MCS_MULTISELECT.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMonthCalCtrl:SetMaxSelCount](#setmaxselcount).

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth

Récupère la largeur maximale de la chaîne "Aujourd’hui" pour le contrôle du calendrier du mois en cours.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la chaîne "Aujourd’hui", en pixels.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code `GetMaxTodayWidth` suivant montre la méthode.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Notes

L’utilisateur peut revenir à la date actuelle en cliquant sur la chaîne "Aujourd’hui", qui s’affiche au bas du contrôle du calendrier du mois. La chaîne "Aujourd’hui" comprend le texte d’étiquette et le texte de date.

Cette méthode envoie le [message MCM_GETMAXTODAYWIDTH,](/windows/win32/Controls/mcm-getmaxtodaywidth) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect

Récupère la taille minimale requise pour afficher un mois complet dans un contrôle de calendrier de mois.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Paramètres

*pRect (en)*<br/>
Un pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui recevra des informations de rectangle de délimitation. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

En cas de succès, cette `lpRect` fonction de membre renvoie nonzero et reçoit les informations de délimitation applicables. En cas d’échec, la fonction du membre renvoie 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect), tel que décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta

Récupère le taux de défilement pour un contrôle de calendrier de mois.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Valeur de retour

Le taux de défilement pour le contrôle du calendrier du mois. Le taux de défilement est le nombre de mois que le contrôle déplace son écran lorsque l’utilisateur clique sur un bouton de défilement une fois.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta), tel que décrit dans le SDK Windows.

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange

Récupère les informations de date représentant les limites élevées et basses de l’affichage d’un contrôle de calendrier de mois.

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>Paramètres

*refMinRange*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant la date minimale autorisée.

*refMaxRange*<br/>
Une référence `COleDateTime` à `CTime` un ou à un objet contenant la date maximale autorisée.

*pMinRange*<br/>
Un pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus basse de la plage.

*pMaxRange (en)*<br/>
Un pointeur `SYSTEMTIME` à une structure contenant la date à l’extrémité la plus élevée de la gamme.

*dwFlags*<br/>
Valeur spécifiant la portée des limites de portée à récupérer. Cette valeur doit être l’une des suivantes.

|Value|Signification|
|-----------|-------------|
|GMR_DAYSTATE|Inclure des mois de plage visibles qui précèdent et qui traînent qui ne sont que partiellement affichés.|
|GMR_VISIBLE|N’incluez que les mois qui sont entièrement affichés.|

### <a name="return-value"></a>Valeur de retour

Un intégrant qui représente la gamme, en mois, s’étend par les deux limites indiquées par *refMinRange* et *refMaxRange* dans les première et deuxième versions, ou *pMinRange* et *pMaxRange* dans la troisième version.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange), tel que décrit dans le SDK Windows. Dans la mise en `GetMonthRange`œuvre `COleDateTime` de `CTime` MFC, `SYSTEMTIME` vous pouvez spécifier l’utilisation, une utilisation ou une utilisation de la structure.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMonthCalCtrl:SetDayState](#setdaystate).

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange

Récupère les dates minimales et maximales actuelles fixées dans un contrôle de calendrier de mois.

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Paramètres

*pMinRange*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus basse de la plage.

*pMaxRange (en)*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Un DWORD qui peut être nul (aucune limite n’est définie) ou une combinaison des valeurs suivantes qui spécifient des informations limites.

|Value|Signification|
|-----------|-------------|
|GDTR_MAX|Une limite maximale est fixée pour le contrôle; *pMaxRange* est valide et contient les informations de date applicables.|
|GDTR_MIN|Une limite minimale est fixée pour le contrôle; *pMinRange* est valide et contient les informations de date applicables.|

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange), tel que décrit dans le SDK Windows. Dans la mise en `GetRange`œuvre `COleDateTime` de MFC, vous pouvez spécifier une utilisation, une `CTime` utilisation ou une `SYSTEMTIME` utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange

Récupère les informations de date représentant les limites supérieures et inférieures de la plage de date actuellement sélectionnées par l’utilisateur.

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>Paramètres

*refMinRange*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant la date minimale autorisée.

*refMaxRange*<br/>
Une référence `COleDateTime` à `CTime` un ou à un objet contenant la date maximale autorisée.

*pMinRange*<br/>
Un pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus basse de la plage.

*pMaxRange (en)*<br/>
Un pointeur `SYSTEMTIME` à une structure contenant la date à l’extrémité la plus élevée de la gamme.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange), tel que décrit dans le SDK Windows. `GetSelRange`échouera s’il est appliqué à un contrôle de calendrier de mois qui n’utilise pas le style MCS_MULTISELECT.

Dans la mise en `GetSelRange`œuvre `COleDateTime` de `CTime` MFC, `SYSTEMTIME` vous pouvez spécifier l’utilisation, une utilisation ou une utilisation de la structure.

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday

Récupère les informations de date pour la date spécifiée comme "aujourd’hui" pour un contrôle de calendrier de mois.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) indiquant le jour en cours.

*pDateTime (en)*<br/>
Un pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui recevra les informations de date. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday), tel que décrit dans le SDK Windows. Dans la mise en `GetToday`œuvre `COleDateTime` de MFC, vous pouvez spécifier une utilisation, une `CTime` utilisation ou une `SYSTEMTIME` utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest

Détermine quel contrôle de calendrier de mois, le cas échéant, se trouve à une position spécifiée.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Paramètres

*pMCHitTest (en)*<br/>
Un pointeur vers une structure [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) contenant des points d’essai de frappe pour le contrôle du calendrier du mois.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD. Égal au membre **uHit** de la `MCHITTESTINFO` structure.

### <a name="remarks"></a>Notes

`HitTest`utilise `MCHITTESTINFO` la structure, qui contient des informations sur le test à succès.

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView

Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue du siècle.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vue actuelle est la vue du siècle; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) qui est décrit dans le SDK Windows. Si ce message renvoie MCMV_CENTURY, cette méthode renvoie TRUE.

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView

Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue de la décennie.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le point de vue actuel est le point de vue de la décennie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) qui est décrit dans le SDK Windows. Si ce message renvoie MCMV_DECADE, cette méthode renvoie TRUE.

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView

Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue du mois.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vue actuelle est la vue du mois; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) qui est décrit dans le SDK Windows. Si ce message renvoie MCMV_MONTH, cette méthode renvoie TRUE.

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView

Indique si la vue actuelle du contrôle du calendrier du mois en cours est la vue de l’année.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vue actuelle est la vue d’année; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_GETCURRENTVIEW,](/windows/win32/Controls/mcm-getcurrentview) qui est décrit dans le SDK Windows. Si ce message renvoie MCMV_YEAR, cette méthode renvoie TRUE.

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder

Définit la largeur de la bordure du contrôle du calendrier du mois en cours.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*cxyBorder (en)*|[dans] La largeur de la bordure, en pixels.|

### <a name="remarks"></a>Notes

Si cette méthode réussit, la largeur de la bordure est réglée sur le paramètre *cxyBorder.* Dans le cas contraire, la largeur de la frontière est réinitialisée à la valeur par défaut qui est spécifiée par le [thème](/windows/win32/Controls/visual-styles-overview)actuel, ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le [message MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit la largeur de la bordure du contrôle du calendrier du mois à huit pixels. Utilisez la méthode [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) pour déterminer si cette méthode a réussi.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault

Définit la largeur par défaut de la bordure du contrôle du calendrier du mois en cours.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Notes

La largeur de la bordure est définie à la valeur par défaut spécifiée par le [thème](/windows/win32/Controls/visual-styles-overview)actuel, ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le [message MCM_SETCALENDARBORDER,](/windows/win32/Controls/mcm-setcalendarborder) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID

Définit l’identifiant du calendrier pour le contrôle du calendrier du mois en cours.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*calid*|[dans] Une des constantes [d’identification](/windows/win32/Intl/calendar-identifiers) de calendrier.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Un identificateur de calendrier spécifie un calendrier spécifique à la région, comme les calendriers grégoriens (localisés), japonais ou Hijri. Utilisez `SetCalID` la méthode pour afficher un calendrier spécifié par le paramètre *étalé* si le lieu qui contient le calendrier est installé sur votre ordinateur.

Cette méthode envoie le [message MCM_SETCALID,](/windows/win32/Controls/mcm-setcalid) qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle du calendrier du mois pour afficher le calendrier de l’ère de l’empereur japonais. La `SetCalID` méthode ne réussit que si ce calendrier est installé sur votre ordinateur.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView

Définit le contrôle du calendrier du mois en cours pour afficher la vue du siècle.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue à `MCMV_CENTURY`, qui représente la vue du siècle.

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor

Définit la couleur d’une zone spécifiée d’un contrôle de calendrier de mois.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*nRégion*<br/>
Une valeur d’intégrage spécifiant quelle couleur de calendrier de mois à définir. Cette valeur peut être l’une des suivantes.

|Value|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|La couleur de fond affichée entre les mois.|
|MCSC_MONTHBK|La couleur de fond affichée dans le mois.|
|MCSC_TEXT|La couleur utilisée pour afficher le texte dans un mois.|
|MCSC_TITLEBK|La couleur de fond affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|La couleur utilisée pour afficher le texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|La couleur utilisée pour afficher l’en-tête et le texte de la journée de fuite. Les jours d’en-tête et les jours de fuite sont les jours des mois précédents et suivants qui apparaissent sur le calendrier actuel.|

*ref*<br/>
Une valeur COLORREF pour le nouveau réglage de couleur pour la partie spécifiée du contrôle du calendrier du mois.

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente le réglage de couleur précédent pour la partie spécifiée du contrôle du calendrier du mois, si elle est réussie. Sinon, ce message renvoie -1.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView

Définit le contrôle du calendrier du mois en cours pour afficher la vue spécifiée.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwNewView (en)*|[dans] L’une des valeurs suivantes qui spécifie une vision mensuelle, annuelle, décennie ou siècle.<br /><br /> MCMV_MONTH: Vue mensuelle<br /><br /> MCMV_YEAR : Vue annuelle<br /><br /> MCMV_DECADE: Vue de la décennie<br /><br /> MCMV_CENTURY: Vue du siècle|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message MCM_SETCURRENTVIEW,](/windows/win32/Controls/mcm-setcurrentview) qui est décrit dans le SDK Windows.

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel

Définit la date actuellement sélectionnée pour un contrôle de calendrier de mois.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) indiquant le contrôle du calendrier du mois actuellement sélectionné.

*pDateTime (en)*<br/>
Pointeur vers une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient la date à définir comme la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel), tel que décrit dans le SDK Windows. Dans la mise en `SetCurSel`œuvre `COleDateTime` de MFC, vous pouvez spécifier une utilisation, une `CTime` utilisation ou une `SYSTEMTIME` utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl::SetDayState

Définit l’affichage pendant des jours dans un contrôle de calendrier de mois.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Paramètres

*nMonths*<br/>
Valeur indiquant combien d’éléments sont dans le tableau qui *pStates* points à.

*p États-Unis*<br/>
Un pointeur à un tableau [monthDAYSTATE](/windows/win32/Controls/monthdaystate) de valeurs qui définissent la façon dont le contrôle du calendrier du mois dessinera chaque jour dans son affichage. Le type de données MONTHDAYSTATE est un peu de champ, où chaque bit (1 à 31) représente l’état d’une journée dans un mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView

Définit le contrôle du calendrier du mois en cours à la vue de la décennie.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue à `MCMV_DECADE`, qui représente la vue de la décennie.

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek

Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Paramètres

*iDay (en)*<br/>
Une valeur integer représentant quel jour doit être fixé comme le premier jour de la semaine. Cette valeur doit être l’un des numéros de jour. Voir [GetFirstDayOfWeek](#getfirstdayofweek) pour une description des numéros de jour.

*lpnOld*<br/>
Un pointeur à un intégreur indiquant le premier jour de la semaine précédemment fixé.

### <a name="return-value"></a>Valeur de retour

Nonzero si le premier jour précédent de la semaine est fixé à une valeur autre que celle de LOCALE_IFIRSTDAYOFWEEK, qui est le jour indiqué dans le paramètre du panneau de contrôle. Sinon, cette fonction revient 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount

Définit le nombre maximum de jours qui peuvent être sélectionnés dans un contrôle de calendrier de mois.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Paramètres

*Nmax*<br/>
La valeur qui sera définie pour représenter le nombre maximum de jours sélectionnables.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta

Définit le taux de défilement pour un contrôle de calendrier de mois.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Paramètres

*iDelta (en anglais)*<br/>
Le nombre de mois à définir comme taux de défilement du contrôle. Si cette valeur est nulle, le delta du mois est réinitialisé par défaut, c’est-à-dire le nombre de mois affichés dans le contrôle.

### <a name="return-value"></a>Valeur de retour

Le taux de parchemin précédent. Si le taux de parchemin n’a pas été défini auparavant, la valeur de retour est de 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta), tel que décrit dans le SDK Windows.

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView

Définit le contrôle du calendrier du mois en cours pour afficher la vue du mois.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue sur MCMV_MONTH, qui représente la vue du mois.

### <a name="example"></a>Exemple

L’exemple de code suivant `m_monthCalCtrl`définit la variable, qui est utilisée pour accéder programmatiquement au contrôle du calendrier du mois. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle du calendrier des mois pour afficher les vues du mois, de l’année, de la décennie et du siècle.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange

Définit les dates minimales et maximales autorisées pour un contrôle de calendrier de mois.

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Paramètres

*pMinRange*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus basse de la plage.

*pMaxRange (en)*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou `SYSTEMTIME` une structure contenant la date à l’extrémité la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange), tel que décrit dans le SDK Windows. Dans la mise en `SetRange`œuvre `COleDateTime` de `CTime` MFC, `SYSTEMTIME` vous pouvez spécifier l’utilisation, une utilisation ou une utilisation de la structure.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMonthCalCtrl:GetRange](#getrange).

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange

Définit la sélection pour un contrôle de calendrier d’un mois à une plage de date donnée.

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>Paramètres

*pMinRange*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à l’extrémité la plus basse de la plage.

*pMaxRange (en)*<br/>
Un pointeur `COleDateTime` vers `CTime` un objet, un objet ou `SYSTEMTIME` une structure contenant la date à l’extrémité la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange), tel que décrit dans le SDK Windows. Dans la mise en `SetSelRange`œuvre `COleDateTime` de `CTime` MFC, `SYSTEMTIME` vous pouvez spécifier l’utilisation, une utilisation ou une utilisation de la structure.

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday

Définit le contrôle du calendrier pour le jour en cours.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient la date actuelle.

*pDateTime (en)*<br/>
Dans la deuxième version, un pointeur d’un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) contenant les informations de date actuelles. Dans la troisième version, un pointeur d’une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient les informations de date actuelles.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMonthCalCtrl:GetToday](#gettoday).

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView

Définit le contrôle du calendrier du mois en cours à la vue de l’année.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue sur MCMV_YEAR, ce qui représente la vue annuelle.

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq

Affiche le contrôle du calendrier du mois à la taille minimale qui s’affiche un mois.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRepaint (en anglais)*<br/>
Précise si le contrôle doit être repeint. Par défaut, TRUE. Si FALSE, aucun repeindre ne se produit.

### <a name="return-value"></a>Valeur de retour

Nonzero si le contrôle du calendrier du mois est dimensionné à son minimum; sinon 0.

### <a name="remarks"></a>Notes

L’appel `SizeMinReq` affiche avec succès le contrôle du calendrier du mois pendant un mois.

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin

Pour le contrôle du calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui s’adaptent dans un rectangle spécifié.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|[dans] Pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui définit un rectangle qui contient le nombre de calendriers souhaité.|

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui définit un rectangle dont la taille est inférieure ou égale au rectangle défini par le *paramètre lpRect.*

### <a name="remarks"></a>Notes

Cette méthode calcule le nombre de calendriers qui peuvent s’adapter dans le rectangle spécifié par le *paramètre lpRect,* puis renvoie le plus petit rectangle qui peut contenir ce nombre de calendriers. En effet, cette méthode réduit le rectangle spécifié pour s’adapter exactement au nombre de calendriers souhaité.

Cette méthode envoie le [message MCM_SIZERECTTOMIN,](/windows/win32/Controls/mcm-sizerecttomin) qui est décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl, classe](../../mfc/reference/cdatetimectrl-class.md)
