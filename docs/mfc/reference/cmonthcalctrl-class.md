---
title: CMonthCalCtrl (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537cbe3f1ccf563114f5a32f61cafe39e8006746
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078139"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (classe)

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
|[CMonthCalCtrl::Create](#create)|Crée un contrôle month calendar et l’attache à la `CMonthCalCtrl` objet.|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Récupère la largeur de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Récupère le nombre de calendriers affichés dans le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Récupère des informations sur le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::GetCalID](#getcalid)|Récupère l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::GetColor](#getcolor)|Obtient la couleur d’une zone spécifiée d’un contrôle month calendar.|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Récupère la vue qui est actuellement affichée par le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::GetCurSel](#getcursel)|Récupère l’heure système, comme indiqué par la date actuellement sélectionnée.|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Récupère le nombre maximal actuel de jours qui peuvent être sélectionnées dans un contrôle month calendar.|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Récupère la largeur maximale de la chaîne « Today » pour le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Récupère la taille minimale nécessaire pour afficher un mois complet dans un contrôle month calendar.|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Récupère la vitesse de défilement pour un contrôle month calendar.|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Récupère les informations représentant les limites de haute et bas de l’affichage d’un contrôle de calendrier de mois de date.|
|[CMonthCalCtrl::GetRange](#getrange)|Récupère les dates minimales et maximales actuelles définies dans un contrôle month calendar.|
|[CMonthCalCtrl::GetSelRange](#getselrange)|Récupère les informations de date représentant les limites supérieures et inférieures de la plage de dates actuellement sélectionnée par l’utilisateur.|
|[CMonthCalCtrl::GetToday](#gettoday)|Récupère les informations de date pour la date spécifiée en tant que « aujourd'hui » pour un contrôle month calendar.|
|[CMonthCalCtrl::HitTest](#hittest)|Détermine quelle section d’un contrôle month calendar est à un moment donné sur l’écran.|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue siècle.|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue de dix ans.|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue du mois.|
|[CMonthCalCtrl::IsYearView](#isyearview)|Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue de l’année.|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Définit la largeur de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Définit la largeur par défaut de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl::SetCalID](#setcalid)|Définit l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Définit le contrôle calendrier du mois en cours pour afficher la vue siècle.|
|[CMonthCalCtrl::SetColor](#setcolor)|Définit la couleur d’une zone spécifiée d’un contrôle month calendar.|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Définit le contrôle calendrier du mois en cours pour afficher la vue spécifiée.|
|[CMonthCalCtrl::SetCurSel](#setcursel)|Définit la date actuellement sélectionnée pour un contrôle month calendar.|
|[CMonthCalCtrl::SetDayState](#setdaystate)|Définit l’affichage pour les jours dans un contrôle month calendar.|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Définit le calendrier du mois actuel contrôle à la vue des dix dernières années.|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Définit le jour de semaine à afficher dans la colonne la plus à gauche du calendrier.|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Définit le nombre maximal de jours qui peuvent être sélectionnées dans un contrôle month calendar.|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Définit la vitesse de défilement pour un contrôle month calendar.|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Définit le contrôle calendrier du mois en cours pour afficher la vue du mois.|
|[CMonthCalCtrl::SetRange](#setrange)|Définit les valeurs minimale et la valeur maximale autorisée de dates pour un contrôle month calendar.|
|[CMonthCalCtrl::SetSelRange](#setselrange)|Définit la sélection d’un calendrier de mois contrôle à une plage de dates donnée.|
|[CMonthCalCtrl::SetToday](#settoday)|Définit le contrôle de calendrier pour le jour actuel.|
|[CMonthCalCtrl::SetYearView](#setyearview)|Définit le calendrier du mois actuel contrôler à la vue de l’année.|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Repeint le calendrier du mois contrôle à sa taille minimale d’un mois.|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.|

## <a name="remarks"></a>Notes

Contrôle month calendar fournit à l’utilisateur avec une interface de calendrier simple, à partir de laquelle l’utilisateur peut sélectionner une date. L’utilisateur peut modifier l’affichage par :

- Défilement vers l’arrière et avant, à partir de mois en mois.

- En cliquant sur le texte aujourd'hui pour afficher la date du jour (si le style MCS_NOTODAY n’est pas utilisé).

- Choisir un mois ou une année à partir d’un menu contextuel.

Vous pouvez personnaliser le mois contrôle calendar en appliquant des styles à l’objet lors de sa création. Ces styles sont décrites dans [Styles de contrôle Month Calendar](/windows/desktop/Controls/month-calendar-control-styles) dans le SDK Windows.

Contrôle month calendar peut afficher plusieurs mois, et il peut indiquer les jours spéciaux (tels que les jours fériés) à mettre en gras la date.

Pour plus d’informations sur l’utilisation du contrôle month calendar, consultez [à l’aide de CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdtctl.h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

Construit un objet `CMonthCalCtrl`.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler `Create` après avoir construit l’objet.

##  <a name="create"></a>  CMonthCalCtrl::Create

Crée un contrôle month calendar et l’attache à la `CMonthCalCtrl` objet.

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

*dwStyle*<br/>
Spécifie la combinaison de styles de Windows appliqués au contrôle month calendar. Consultez [Styles de contrôle Month Calendar](/windows/desktop/Controls/month-calendar-control-styles) dans le SDK Windows pour plus d’informations sur les styles.

*Rect*<br/>
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure. Contient la position et la taille du contrôle month calendar.

*pt*<br/>
Une référence à un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure qui identifie l’emplacement du contrôle month calendar.

*pParentWnd*<br/>
Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle month calendar. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle. du contrôle month calendar

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’initialisation a abouti ; sinon 0.

### <a name="remarks"></a>Notes

Créer un mois du calendrier contrôle en deux étapes :

1. Appelez [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) pour construire un `CMonthCalCtrl` objet.

1. Appelez cette fonction membre, ce qui crée un contrôle month calendar et l’attache à la `CMonthCalCtrl` objet.

Lorsque vous appelez `Create`, les contrôles communs sont initialisés. La version de `Create` vous appel détermine la façon dont il est dimensionné :

- Pour que MFC automatiquement la taille du contrôle à un mois, appelle la substitution qui utilise le *pt* paramètre.

- Pour redimensionner le contrôle vous-même, appelle la substitution de cette fonction qui utilise le *rect* paramètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

Récupère la largeur de la bordure du contrôle calendrier du mois en cours.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la bordure du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder) message, qui est décrite dans le SDK Windows.

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

Récupère le nombre de calendriers affichés dans le contrôle de calendrier du mois en cours.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de calendriers actuellement affichée dans le contrôle calendrier du mois. Le nombre maximal autorisé de calendriers est 12.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount) message, qui est décrite dans le SDK Windows.

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

Récupère des informations sur le contrôle de calendrier du mois en cours.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pmcGridInfo*|[out] Pointeur vers un [MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo) structure qui reçoit des informations sur le contrôle de calendrier du mois en cours. L’appelant est chargé d’allouer et de l’initialisation de cette structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

Le code suivant exemple utilise le `GetCalendarGridInfo` méthode pour récupérer la date de calendrier qui affiche le contrôle de calendrier du mois en cours.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

Récupère l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Valeur de retour

Parmi les [identificateur de calendrier](/windows/desktop/Intl/calendar-identifiers) constantes.

### <a name="remarks"></a>Notes

Un identificateur de calendrier désigne un calendrier spécifiques à une région, tels que le calendrier grégorien (localisé), japonais ou Hijri calendriers. Votre application peut utiliser un identificateur de calendrier qui a en différents langages prennent en charge des fonctions.

Cette méthode envoie le [MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid) message, qui est décrite dans le SDK Windows.

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

Récupère la couleur d’une zone du mois du calendrier contrôle spécifié par *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Paramètres

*nRegion*<br/>
La région du contrôle month calendar à partir de laquelle la couleur est récupérée. Pour obtenir la liste de valeurs, consultez le *nRegion* paramètre de [SetColor](#setcolor).

### <a name="return-value"></a>Valeur de retour

Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui spécifie la couleur associée à la partie du contrôle month calendar, en cas de réussite. Sinon, cette fonction membre retourne -1.

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

Récupère la vue qui est actuellement affichée par le contrôle de calendrier du mois en cours.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Valeur de retour

La vue actuelle, ce qui est indiquée par une des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|MCMV_MONTH|Vue mensuelle|
|MCMV_YEAR|Vue annuel|
|MCMV_DECADE|Affichage des dix dernières années|
|MCMV_CENTURY|Vue de siècle|

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

Les rapports d’exemple de code suivant qui permet d’afficher le calendrier du mois contrôlent qui affiche actuellement.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

Récupère l’heure système, comme indiqué par la date actuellement sélectionnée.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet ou un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet. Reçoit l’heure actuelle.

*pDateTime*<br/>
Un pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui recevra les informations de date actuellement sélectionnée. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; otherwize 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel), comme décrit dans le SDK Windows.

> [!NOTE]
>  Cette fonction membre échoue si le style MCS_MULTISELECT est défini.

Dans l’implémentation MFC de `GetCurSel`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbLocal*<br/>
Pointeur vers une valeur BOOL. Si la valeur est différente de zéro, le paramètre de contrôle ne correspond pas au paramètre dans le panneau de configuration.

### <a name="return-value"></a>Valeur de retour

Valeur entière qui représente le premier jour de la semaine. Consultez **remarques** pour plus d’informations sur ce que représentent ces entiers.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek), comme décrit dans le SDK Windows. Les jours de la semaine sont représentés sous forme d’entiers, comme suit.

|Value|Jour de la semaine|
|-----------|---------------------|
|0|Le lundi|
|1|Mardi|
|2|Le mercredi|
|3|Jeudi|
|4|Le vendredi|
|5|Saturday|
|6|Dimanche|

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

Récupère le nombre maximal actuel de jours qui peuvent être sélectionnées dans un contrôle month calendar.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur entière qui représente le nombre total de jours qui peuvent être sélectionnés pour le contrôle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount), comme décrit dans le SDK Windows. Utilisez cette fonction membre pour les contrôles avec le jeu de styles MCS_MULTISELECT.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

Récupère la largeur maximale de la chaîne « Today » pour le contrôle de calendrier du mois en cours.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la chaîne « Today », en pixels.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant montre le `GetMaxTodayWidth` (méthode).

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Notes

L’utilisateur peut revenir à la date actuelle en cliquant sur la chaîne « Today », qui s’affiche en bas du contrôle month calendar. La chaîne « Today » inclut le texte d’étiquette et le texte de la date.

Cette méthode envoie le [MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth) message, qui est décrite dans le SDK Windows.

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

Récupère la taille minimale nécessaire pour afficher un mois complet dans un contrôle month calendar.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Paramètres

*pRect*<br/>
Un pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui recevra les informations de rectangle englobant. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Si la réussite, cette fonction membre retourne différente de zéro et `lpRect` reçoit les informations englobantes applicables. En cas d’échec, la fonction membre retourne 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect), comme décrit dans le SDK Windows.

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

Récupère la vitesse de défilement pour un contrôle month calendar.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Valeur de retour

La vitesse de défilement du contrôle month calendar. La vitesse de défilement est le nombre de mois que le contrôle déplace son affichage lorsque l’utilisateur clique sur un bouton de défilement en une seule fois.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta), comme décrit dans le SDK Windows.

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

Récupère les informations représentant les limites de haute et bas de l’affichage d’un contrôle de calendrier de mois de date.

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
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la date minimale autorisée.

*refMaxRange*<br/>
Une référence à un `COleDateTime` ou `CTime` objet contenant la date maximale autorisée.

*pMinRange*<br/>
Un pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.

*pMaxRange*<br/>
Un pointeur vers un `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.

*dwFlags*<br/>
Valeur spécifiant la portée de la plage de limite à récupérer. Cette valeur doit être une des opérations suivantes.

|Value|Signification|
|-----------|-------------|
|GMR_DAYSTATE|Inclure précédent et de fin de mois de la plage visible que partiellement affichés.|
|GMR_VISIBLE|Inclure uniquement ces mois entièrement affichés.|

### <a name="return-value"></a>Valeur de retour

Entier qui représente la plage, en mois, couvertes par les deux limites indiqué par *refMinRange* et *refMaxRange* dans les versions de première et deuxième, ou *pMinRange* et *pMaxRange* dans la troisième version.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetMonthRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl::SetDayState](#setdaystate).

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

Récupère les dates minimales et maximales actuelles définies dans un contrôle month calendar.

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
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.

*pMaxRange*<br/>
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD qui peut être zéro (sans limitation de la valeur) ou une combinaison des valeurs suivantes qui spécifient les informations de limite.

|Value|Signification|
|-----------|-------------|
|GDTR_MAX|Une limite maximale est définie pour le contrôle ; *pMaxRange* est valide et contient les informations de date applicable.|
|GDTR_MIN|Une limite minimale est définie pour le contrôle ; *pMinRange* est valide et contient les informations de date applicable.|

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetRange`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

Récupère les informations de date représentant les limites supérieures et inférieures de la plage de dates actuellement sélectionnée par l’utilisateur.

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
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la date minimale autorisée.

*refMaxRange*<br/>
Une référence à un `COleDateTime` ou `CTime` objet contenant la date maximale autorisée.

*pMinRange*<br/>
Un pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.

*pMaxRange*<br/>
Un pointeur vers un `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange), comme décrit dans le SDK Windows. `GetSelRange` échoue si appliqué à un contrôle month calendar qui n’utilise pas le style MCS_MULTISELECT.

Dans l’implémentation MFC de `GetSelRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

Récupère les informations de date pour la date spécifiée en tant que « aujourd'hui » pour un contrôle month calendar.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet indiquant la date du jour.

*pDateTime*<br/>
Un pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui recevra les informations de date. Ce paramètre doit être une adresse valide et ne peut pas être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetToday`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

Détermine quel contrôle month calendar, si une, est à la position spécifiée.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Paramètres

*pMCHitTest*<br/>
Un pointeur vers un [MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo) pointe de structure qui contient le test de positionnement pour un contrôle month calendar.

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD. Égal à la **uHit** membre de la `MCHITTESTINFO` structure.

### <a name="remarks"></a>Notes

`HitTest` utilise le `MCHITTESTINFO` structure qui contient des informations sur le test de positionnement.

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue siècle.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue siècle ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) message, qui est décrite dans le SDK Windows. Si ce message renvoie MCMV_CENTURY, cette méthode retourne la valeur TRUE.

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue de dix ans.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue des dix dernières années ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) message, qui est décrite dans le SDK Windows. Si ce message renvoie MCMV_DECADE, cette méthode retourne la valeur TRUE.

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue du mois.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue du mois ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) message, qui est décrite dans le SDK Windows. Si ce message renvoie MCMV_MONTH, cette méthode retourne la valeur TRUE.

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

Indique si l’affichage actuel du contrôle calendrier du mois en cours est la vue de l’année.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue de l’année ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview) message, qui est décrite dans le SDK Windows. Si ce message renvoie MCMV_YEAR, cette méthode retourne la valeur TRUE.

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

Définit la largeur de la bordure du contrôle calendrier du mois en cours.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*cxyBorder*|[in] La largeur de la bordure, en pixels.|

### <a name="remarks"></a>Notes

Si cette méthode réussit, la largeur de bordure est définie le *cxyBorder* paramètre. Sinon, la largeur de bordure est réinitialisée à la valeur par défaut qui est spécifiée par l’actuel [thème](/windows/desktop/Controls/visual-styles-overview), ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

Le code exemple suivant définit la largeur de bordure du calendrier du mois le contrôle à huit pixels. Utilisez le [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) méthode pour déterminer si cette méthode a réussi.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

Définit la largeur par défaut de la bordure du contrôle calendrier du mois en cours.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Notes

La largeur de bordure est définie sur la valeur par défaut spécifiée par l’actuel [thème](/windows/desktop/Controls/visual-styles-overview), ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder) message, qui est décrite dans le SDK Windows.

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

Définit l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*calID*|[in] Parmi les [identificateur de calendrier](/windows/desktop/Intl/calendar-identifiers) constantes.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Un identificateur de calendrier indique un calendrier spécifiques à une région, tels que le calendrier grégorien (localisé), japonais ou Hijri calendriers. Utilisez le `SetCalID` méthode pour afficher un calendrier spécifié par le *calid* paramètre si les paramètres régionaux contenant le calendrier sont installé sur votre ordinateur.

Cette méthode envoie le [MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid) message, qui est décrite dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle month calendar pour afficher le Calendrier impérial japonais. Le `SetCalID` méthode réussit uniquement si ce calendrier est installé sur votre ordinateur.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

Définit le contrôle calendrier du mois en cours pour afficher la vue siècle.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la [CMonthCalCtrl::SetCurrentView](#setcurrentview) méthode pour définir la vue `MCMV_CENTURY`, qui représente la vue siècle.

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

Définit la couleur d’une zone spécifiée d’un contrôle month calendar.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*nRegion*<br/>
Valeur entière spécifiant la couleur de calendrier de mois à définir. Cette valeur peut être une des opérations suivantes.

|Value|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|La couleur d’arrière-plan affichée entre les mois.|
|MCSC_MONTHBK|La couleur d’arrière-plan affichée dans le mois.|
|MCSC_TEXT|La couleur utilisée pour afficher le texte au sein d’un mois.|
|MCSC_TITLEBK|La couleur d’arrière-plan affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|La couleur utilisée pour afficher du texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|La couleur utilisée pour afficher le texte d’en-tête et le jour de fin. Les jours précédents et sont les jours des mois précédents et suivants qui s’affichent sur le calendrier actuel.|

*ref*<br/>
Valeur COLORREF pour le nouveau paramètre de couleur pour la partie spécifiée du contrôle month calendar.

### <a name="return-value"></a>Valeur de retour

Une valeur COLORREF qui représente le paramètre précédent de la couleur pour la partie spécifiée du contrôle month calendar, en cas de réussite. Dans le cas contraire, ce message retourne -1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

Définit le contrôle calendrier du mois en cours pour afficher la vue spécifiée.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwNewView*|[in] Une des valeurs suivantes qui spécifie un mensuelle, annuelle, des dix dernières années ou siècle vue.<br /><br /> MCMV_MONTH : Vue mensuelle<br /><br /> MCMV_YEAR : Vue annuel<br /><br /> MCMV_DECADE : Affichage des dix dernières années<br /><br /> MCMV_CENTURY : Vue de siècle|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode envoie le [MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview) message, qui est décrite dans le SDK Windows.

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

Définit la date actuellement sélectionnée pour un contrôle month calendar.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui indique le contrôle de calendrier du mois sélectionné.

*pDateTime*<br/>
Pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à définir en tant que la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetCurSel`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState

Définit l’affichage pour les jours dans un contrôle month calendar.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Paramètres

*nMonths*<br/>
Valeur qui indique le nombre d’éléments présents dans le tableau qui *pStates* pointe vers.

*pStates*<br/>
Un pointeur vers un [MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate) tableau de valeurs qui définissent la façon dont le contrôle month calendar dessine chaque jour dans son affichage. Le type de données MONTHDAYSTATE est un champ de bits, où chaque bit (1 à 31) représente l’état d’un jour dans un mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

Définit le calendrier du mois actuel contrôle à la vue des dix dernières années.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la [CMonthCalCtrl::SetCurrentView](#setcurrentview) méthode pour définir la vue `MCMV_DECADE`, qui représente la vue des dix dernières années.

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

Définit le jour de semaine à afficher dans la colonne la plus à gauche du calendrier.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Paramètres

*iDay*<br/>
Valeur entière représentant le jour doit être défini comme le premier jour de la semaine. Cette valeur doit être un des numéros de jour. Consultez [GetFirstDayOfWeek](#getfirstdayofweek) pour obtenir une description des numéros de jour.

*lpnOld*<br/>
Pointeur vers un entier indiquant le premier jour de la semaine précédemment définie.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le premier jour de la semaine précédent est défini sur une valeur différente de celle de LOCALE_IFIRSTDAYOFWEEK, qui est le jour indiqué dans le panneau de configuration de contrôle. Sinon, cette fonction retourne 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

Définit le nombre maximal de jours qui peuvent être sélectionnées dans un contrôle month calendar.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Paramètres

*nombre maximal*<br/>
La valeur qui sera définie pour représenter le nombre maximal de jours pouvant être sélectionnées.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

Définit la vitesse de défilement pour un contrôle month calendar.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Paramètres

*iDelta*<br/>
Le nombre de mois à définir comme la vitesse de défilement du contrôle. Si cette valeur est zéro, le delta de mois est réinitialisé à la valeur par défaut, ce qui correspond au nombre de mois à afficher dans le contrôle.

### <a name="return-value"></a>Valeur de retour

La vitesse de défilement précédente. Si la vitesse de défilement n’a pas été définie précédemment, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta), comme décrit dans le SDK Windows.

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

Définit le contrôle calendrier du mois en cours pour afficher la vue du mois.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la [CMonthCalCtrl::SetCurrentView](#setcurrentview) méthode pour définir la vue à MCMV_MONTH, qui représente la vue du mois.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programmation le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle month calendar pour afficher le mois, année, des dix dernières années et les vues siècle.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

Définit les dates autorisées minimales et maximales pour un contrôle month calendar.

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
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.

*pMaxRange*<br/>
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl::GetRange](#getrange).

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

Définit la sélection d’un calendrier de mois contrôle à une plage de dates donnée.

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
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.

*pMaxRange*<br/>
Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange), comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetSelRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` l’utilisation de la structure.

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

Définit le contrôle de calendrier pour le jour actuel.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
  void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui contient la date actuelle.

*pDateTime*<br/>
Dans la deuxième version, un pointeur vers un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant les informations de date actuelle. Dans la troisième version, un pointeur vers un [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient les informations de date actuelle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday), comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl::GetToday](#gettoday).

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

Définit le calendrier du mois actuel contrôler à la vue de l’année.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise la [CMonthCalCtrl::SetCurrentView](#setcurrentview) méthode pour définir la vue à MCMV_YEAR, qui représente la vue annuelle.

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

Affiche le mois de contrôle de calendrier à la valeur minimale de taille qui affiche un mois.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRepaint*<br/>
Spécifie si le contrôle doit être repeinte. Par défaut, la valeur TRUE. Si la valeur est FALSE, aucune mise à jour se produit.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contrôle month calendar a une taille minimale ; sinon 0.

### <a name="remarks"></a>Notes

Appel `SizeMinReq` affiche correctement le contrôle de calendrier du mois pour le calendrier d’un mois.

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|[in] Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui définit un rectangle qui contient le nombre souhaité de calendriers.|

### <a name="return-value"></a>Valeur de retour

Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui définit un rectangle dont la taille est inférieure ou égale au rectangle défini par le *lpRect* paramètre.

### <a name="remarks"></a>Notes

Cette méthode calcule le nombre de calendriers peut être contenue dans le rectangle spécifié par le *lpRect* paramètre, puis retourne le plus petit rectangle qui peut contenir ce nombre de calendriers. En effet, cette méthode réduit le rectangle spécifié adapte exactement le nombre souhaité de calendriers.

Cette méthode envoie le [MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin) message, qui est décrite dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL1](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl, classe](../../mfc/reference/cdatetimectrl-class.md)
