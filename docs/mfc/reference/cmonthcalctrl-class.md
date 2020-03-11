---
title: CMonthCalCtrl (classe)
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
ms.openlocfilehash: 963aecfed4f6eb67a0ab227df06fce98c0778f7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866388"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (classe)

Encapsule les fonctionnalités d'un contrôle Month Calendar.

## <a name="syntax"></a>Syntaxe

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CMonthCalCtrl :: CMonthCalCtrl](#cmonthcalctrl)|Construit un objet `CMonthCalCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMonthCalCtrl :: Create](#create)|Crée un contrôle Month Calendar et l’attache à l’objet `CMonthCalCtrl`.|
|[CMonthCalCtrl :: GetCalendarBorder](#getcalendarborder)|Récupère la largeur de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetCalendarCount](#getcalendarcount)|Récupère le nombre de calendriers affichés dans le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetCalendarGridInfo](#getcalendargridinfo)|Récupère des informations sur le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetCalID](#getcalid)|Récupère l’identificateur de calendrier pour le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetColor](#getcolor)|Obtient la couleur d’une zone spécifiée d’un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetCurrentView](#getcurrentview)|Récupère la vue actuellement affichée par le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetCurSel](#getcursel)|Récupère l’heure système telle qu’elle est indiquée par la date actuellement sélectionnée.|
|[CMonthCalCtrl :: GetFirstDayOfWeek](#getfirstdayofweek)|Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|
|[CMonthCalCtrl :: GetMaxSelCount](#getmaxselcount)|Récupère le nombre maximal de jours en cours qui peuvent être sélectionnés dans un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetMaxTodayWidth](#getmaxtodaywidth)|Récupère la largeur maximale de la chaîne « aujourd’hui » pour le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: GetMinReqRect](#getminreqrect)|Récupère la taille minimale requise pour afficher un mois complet dans un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetMonthDelta](#getmonthdelta)|Récupère la vitesse de défilement pour un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetMonthRange](#getmonthrange)|Récupère des informations de date représentant les limites haute et basse de l’affichage d’un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetRange](#getrange)|Récupère les dates minimale et maximale actuelles définies dans un contrôle Month Calendar.|
|[CMonthCalCtrl :: GetSelRange](#getselrange)|Récupère des informations de date représentant les limites supérieure et inférieure de la plage de dates actuellement sélectionnée par l’utilisateur.|
|[CMonthCalCtrl :: GetToday](#gettoday)|Récupère les informations de date pour la date spécifiée comme « Today » pour un contrôle Month Calendar.|
|[CMonthCalCtrl :: HitTest](#hittest)|Détermine la section d’un contrôle calendrier du mois qui se trouve à un point donné sur l’écran.|
|[CMonthCalCtrl :: IsCenturyView](#iscenturyview)|Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue du siècle.|
|[CMonthCalCtrl :: IsDecadeView](#isdecadeview)|Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue la plus décennie.|
|[CMonthCalCtrl :: IsMonthView](#ismonthview)|Indique si la vue actuelle du contrôle calendrier du mois en cours est l’affichage du mois.|
|[CMonthCalCtrl :: IsYearView](#isyearview)|Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue Year.|
|[CMonthCalCtrl :: SetCalendarBorder](#setcalendarborder)|Définit la largeur de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: SetCalendarBorderDefault](#setcalendarborderdefault)|Définit la largeur par défaut de la bordure du contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: SetCalID](#setcalid)|Définit l’identificateur de calendrier pour le contrôle calendrier du mois en cours.|
|[CMonthCalCtrl :: SetCenturyView](#setcenturyview)|Définit le contrôle calendrier du mois en cours pour afficher la vue du siècle.|
|[CMonthCalCtrl :: SetColor](#setcolor)|Définit la couleur d’une zone spécifiée d’un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetCurrentView](#setcurrentview)|Définit le contrôle calendrier du mois en cours pour afficher la vue spécifiée.|
|[CMonthCalCtrl :: SetCurSel](#setcursel)|Définit la date actuellement sélectionnée pour un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetDayState](#setdaystate)|Définit l’affichage pour les jours dans un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetDecadeView](#setdecadeview)|Définit le contrôle calendrier du mois en cours sur la vue décennie.|
|[CMonthCalCtrl :: SetFirstDayOfWeek](#setfirstdayofweek)|Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|
|[CMonthCalCtrl :: SetMaxSelCount](#setmaxselcount)|Définit le nombre maximal de jours pouvant être sélectionnés dans un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetMonthDelta](#setmonthdelta)|Définit la vitesse de défilement pour un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetMonthView](#setmonthview)|Définit le contrôle calendrier du mois en cours pour afficher l’affichage du mois.|
|[CMonthCalCtrl :: SetRange](#setrange)|Définit les dates minimale et maximale autorisées pour un contrôle Month Calendar.|
|[CMonthCalCtrl :: SetSelRange](#setselrange)|Définit la sélection d’un contrôle Month Calendar sur une plage de dates donnée.|
|[CMonthCalCtrl :: SetToday](#settoday)|Définit le contrôle calendrier pour le jour actuel.|
|[CMonthCalCtrl :: SetYearView](#setyearview)|Définit le contrôle calendrier du mois en cours sur l’affichage année.|
|[CMonthCalCtrl :: SizeMinReq](#sizeminreq)|Repeint le contrôle Month Calendar à sa taille minimale d’un mois.|
|[CMonthCalCtrl :: SizeRectToMin](#sizerecttomin)|Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.|

## <a name="remarks"></a>Notes

Le contrôle Month Calendar fournit à l’utilisateur une interface de calendrier simple, à partir de laquelle l’utilisateur peut sélectionner une date. L’utilisateur peut modifier l’affichage en :

- Défilement vers l’arrière et vers l’avant, du mois au mois.

- En cliquant sur le texte du jour pour afficher le jour actuel (si le style de MCS_NOTODAY n’est pas utilisé).

- Sélection d’un mois ou d’une année dans un menu contextuel.

Vous pouvez personnaliser le contrôle Month Calendar en appliquant divers styles à l’objet lors de sa création. Ces styles sont décrits dans les [styles du contrôle calendrier du mois](/windows/win32/Controls/month-calendar-control-styles) dans le SDK Windows.

Le contrôle Month Calendar peut afficher plus d’un mois et peut indiquer des jours spéciaux (tels que les jours fériés) en mettant en gras la date.

Pour plus d’informations sur l’utilisation du contrôle Month Calendar, consultez [utilisation de CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDTCTL. h

##  <a name="cmonthcalctrl"></a>CMonthCalCtrl :: CMonthCalCtrl

Construit un objet `CMonthCalCtrl`.

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Notes

Vous devez appeler `Create` une fois que vous avez construit l’objet.

##  <a name="create"></a>CMonthCalCtrl :: Create

Crée un contrôle Month Calendar et l’attache à l’objet `CMonthCalCtrl`.

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
Spécifie la combinaison de styles Windows appliquée au contrôle Month Calendar. Pour plus d’informations sur les styles, consultez [styles du contrôle calendrier mensuel](/windows/win32/Controls/month-calendar-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) . Contient la position et la taille du contrôle Month Calendar.

*pt*<br/>
Référence à une structure [point](/previous-versions/dd162805\(v=vs.85\)) qui identifie l’emplacement du contrôle Month Calendar.

*pParentWnd*<br/>
Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle Month Calendar. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle Month Calendar.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Créez un contrôle Month Calendar en deux étapes :

1. Appelez [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) pour construire un objet `CMonthCalCtrl`.

1. Appelez cette fonction membre, qui crée un contrôle Month Calendar et l’attache à l’objet `CMonthCalCtrl`.

Lorsque vous appelez `Create`, les contrôles communs sont initialisés. La version de `Create` que vous appelez détermine la façon dont elle est dimensionnée :

- Pour que MFC dimensionne automatiquement le contrôle à un mois, appelez la substitution qui utilise le paramètre *PT* .

- Pour dimensionner vous-même le contrôle, appelez la substitution de cette fonction qui utilise le paramètre *Rect* .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>CMonthCalCtrl :: GetCalendarBorder

Récupère la largeur de la bordure du contrôle calendrier du mois en cours.

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la bordure du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder) , qui est décrit dans le SDK Windows.

##  <a name="getcalendarcount"></a>CMonthCalCtrl :: GetCalendarCount

Récupère le nombre de calendriers affichés dans le contrôle calendrier du mois en cours.

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de calendriers actuellement affichés dans le contrôle Month Calendar. Le nombre maximal autorisé de calendriers est 12.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount) , qui est décrit dans le SDK Windows.

##  <a name="getcalendargridinfo"></a>CMonthCalCtrl :: GetCalendarGridInfo

Récupère des informations sur le contrôle calendrier du mois en cours.

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pmcGridInfo*|à Pointeur vers une structure [MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) qui reçoit des informations sur le contrôle calendrier du mois en cours. L’appelant est responsable de l’allocation et de l’initialisation de cette structure.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant utilise la méthode `GetCalendarGridInfo` pour récupérer la date du calendrier affichée par le contrôle calendrier du mois en cours.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>CMonthCalCtrl :: GetCalID

Récupère l’identificateur de calendrier pour le contrôle calendrier du mois en cours.

```
CALID GetCalID() const;
```

### <a name="return-value"></a>Valeur de retour

Une des constantes d' [identificateur de calendrier](/windows/win32/Intl/calendar-identifiers) .

### <a name="remarks"></a>Notes

Un identificateur de calendrier désigne un calendrier spécifique à une région, tel que les calendriers grégoriens (localisés), japonais ou Hijri. Votre application peut utiliser un identificateur de calendrier avec différentes fonctions de prise en charge linguistique.

Cette méthode envoie le message [MCM_GETCALID](/windows/win32/Controls/mcm-getcalid) , qui est décrit dans le SDK Windows.

##  <a name="getcolor"></a>CMonthCalCtrl :: GetColor

Récupère la couleur d’une zone du contrôle Month Calendar spécifié par *nRegion*.

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>Paramètres

*nRegion*<br/>
Région du contrôle Month Calendar à partir duquel la couleur est récupérée. Pour obtenir la liste des valeurs, consultez le paramètre *nRegion* de [setColor](#setcolor).

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) spécifiant la couleur associée à la partie du contrôle Month Calendar, en cas de réussite. Dans le cas contraire, cette fonction membre retourne-1.

##  <a name="getcurrentview"></a>CMonthCalCtrl :: GetCurrentView

Récupère la vue actuellement affichée par le contrôle calendrier du mois en cours.

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>Valeur de retour

Vue actuelle, qui est indiquée par l’une des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|MCMV_MONTH|Affichage mensuel|
|MCMV_YEAR|Vue annuelle|
|MCMV_DECADE|Vue décennie|
|MCMV_CENTURY|Vue du siècle|

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant indique la vue affichée par le contrôle Month Calendar.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>CMonthCalCtrl :: GetCurSel

Récupère l’heure système telle qu’elle est indiquée par la date actuellement sélectionnée.

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) . Reçoit l’heure actuelle.

*pDateTime*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui recevra les informations de date actuellement sélectionnées. Ce paramètre doit être une adresse valide et ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; otherwize 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)de message Win32, comme décrit dans le SDK Windows.

> [!NOTE]
>  Cette fonction membre échoue si le style MCS_MULTISELECT est défini.

Dans l’implémentation MFC de `GetCurSel`, vous pouvez spécifier une utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

##  <a name="getfirstdayofweek"></a>CMonthCalCtrl :: GetFirstDayOfWeek

Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>Paramètres

*pbLocal*<br/>
Pointeur vers une valeur BOOL. Si la valeur est différente de zéro, le paramètre du contrôle ne correspond pas au paramètre dans le panneau de configuration.

### <a name="return-value"></a>Valeur de retour

Valeur entière qui représente le premier jour de la semaine. Pour plus d’informations sur ce que représentent ces entiers, consultez la **section Notes** .

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)de message Win32, comme décrit dans le SDK Windows. Les jours de la semaine sont représentés sous forme d’entiers, comme suit.

|Valeur|Jour de la semaine|
|-----------|---------------------|
|0|Lundi|
|1|Mardi|
|2|Mercredi|
|3|Jeudi|
|4|Vendredi|
|5|Samedi|
|6|Dimanche|

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl :: SetFirstDayOfWeek](#setfirstdayofweek).

##  <a name="getmaxselcount"></a>CMonthCalCtrl :: GetMaxSelCount

Récupère le nombre maximal de jours en cours qui peuvent être sélectionnés dans un contrôle Month Calendar.

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur entière qui représente le nombre total de jours pouvant être sélectionnés pour le contrôle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)de message Win32, comme décrit dans le SDK Windows. Utilisez cette fonction membre pour les contrôles avec le style de MCS_MULTISELECT défini.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl :: SetMaxSelCount](#setmaxselcount).

##  <a name="getmaxtodaywidth"></a>CMonthCalCtrl :: GetMaxTodayWidth

Récupère la largeur maximale de la chaîne « aujourd’hui » pour le contrôle calendrier du mois en cours.

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>Valeur de retour

Largeur de la chaîne « Today », en pixels.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant illustre la méthode `GetMaxTodayWidth`.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Notes

L’utilisateur peut retourner à la date actuelle en cliquant sur la chaîne « aujourd’hui », qui est affichée en bas du contrôle Month Calendar. La chaîne « aujourd’hui » comprend le texte de l’étiquette et le texte de date.

Cette méthode envoie le message [MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth) , qui est décrit dans le SDK Windows.

##  <a name="getminreqrect"></a>CMonthCalCtrl :: GetMinReqRect

Récupère la taille minimale requise pour afficher un mois complet dans un contrôle Month Calendar.

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>Paramètres

*pRect*<br/>
Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui recevra les informations de rectangle englobant. Ce paramètre doit être une adresse valide et ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, cette fonction membre retourne une valeur différente de zéro et `lpRect` reçoit les informations de limite applicables. En cas d’échec, la fonction membre retourne 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getmonthdelta"></a>CMonthCalCtrl :: GetMonthDelta

Récupère la vitesse de défilement pour un contrôle Month Calendar.

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>Valeur de retour

Taux de défilement pour le contrôle Month Calendar. La vitesse de défilement est le nombre de mois pendant lesquels le contrôle déplace son affichage lorsque l’utilisateur clique une fois sur un bouton de défilement.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)de message Win32, comme décrit dans le SDK Windows.

##  <a name="getmonthrange"></a>CMonthCalCtrl :: GetMonthRange

Récupère des informations de date représentant les limites haute et basse de l’affichage d’un contrôle Month Calendar.

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
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant la date minimale autorisée.

*refMaxRange*<br/>
Référence à un objet `COleDateTime` ou `CTime` contenant la date maximale autorisée.

*pMinRange*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus basse de la plage.

*pMaxRange*<br/>
Pointeur vers une structure `SYSTEMTIME` contenant la date à la fin la plus élevée de la plage.

*dwFlags*<br/>
Valeur spécifiant l’étendue des limites de plage à récupérer. Cette valeur doit être l’une des suivantes :

|Valeur|Signification|
|-----------|-------------|
|GMR_DAYSTATE|Inclut les mois précédents et de fin de la plage visible qui ne sont affichés que partiellement.|
|GMR_VISIBLE|Inclut uniquement les mois qui sont entièrement affichés.|

### <a name="return-value"></a>Valeur de retour

Entier qui représente la plage, en mois, fractionnée par les deux limites indiquées par *refMinRange* et *refMaxRange* dans la première et la deuxième version, ou *pMinRange* et *pMaxRange* dans la troisième version.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetMonthRange`, vous pouvez spécifier l’utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl :: SetDayState](#setdaystate).

##  <a name="getrange"></a>CMonthCalCtrl :: GetRange

Récupère les dates minimale et maximale actuelles définies dans un contrôle Month Calendar.

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
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus basse de la plage.

*pMaxRange*<br/>
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur DWORD qui peut être zéro (aucune limite n’est définie) ou une combinaison des valeurs suivantes qui spécifient des informations de limite.

|Valeur|Signification|
|-----------|-------------|
|GDTR_MAX|Une limite maximale est définie pour le contrôle ; *pMaxRange* est valide et contient les informations de date applicables.|
|GDTR_MIN|Une limite minimale est définie pour le contrôle ; *pMinRange* est valide et contient les informations de date applicables.|

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetRange`, vous pouvez spécifier une utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>CMonthCalCtrl :: GetSelRange

Récupère des informations de date représentant les limites supérieure et inférieure de la plage de dates actuellement sélectionnée par l’utilisateur.

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
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant la date minimale autorisée.

*refMaxRange*<br/>
Référence à un objet `COleDateTime` ou `CTime` contenant la date maximale autorisée.

*pMinRange*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus basse de la plage.

*pMaxRange*<br/>
Pointeur vers une structure `SYSTEMTIME` contenant la date à la fin la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)de message Win32, comme décrit dans le SDK Windows. `GetSelRange` échouera s’il est appliqué à un contrôle Month Calendar qui n’utilise pas le style MCS_MULTISELECT.

Dans l’implémentation MFC de `GetSelRange`, vous pouvez spécifier l’utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

##  <a name="gettoday"></a>CMonthCalCtrl :: GetToday

Récupère les informations de date pour la date spécifiée comme « Today » pour un contrôle Month Calendar.

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [ctime](../../atl-mfc-shared/reference/ctime-class.md) indiquant le jour actuel.

*pDateTime*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui recevra les informations de date. Ce paramètre doit être une adresse valide et ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetToday`, vous pouvez spécifier une utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>CMonthCalCtrl :: HitTest

Détermine le contrôle de calendrier mensuel, le cas échéant, à une position spécifiée.

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>Paramètres

*pMCHitTest*<br/>
Pointeur vers une structure [MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo) contenant des points de test de positionnement pour le contrôle Month Calendar.

### <a name="return-value"></a>Valeur de retour

Valeur DWORD. Égal au membre **uHit** de la structure `MCHITTESTINFO`.

### <a name="remarks"></a>Notes

`HitTest` utilise la structure de `MCHITTESTINFO`, qui contient des informations sur le test de positionnement.

##  <a name="iscenturyview"></a>CMonthCalCtrl :: IsCenturyView

Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue du siècle.

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue de siècle ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) , qui est décrit dans le SDK Windows. Si ce message retourne MCMV_CENTURY, cette méthode retourne TRUE.

##  <a name="isdecadeview"></a>CMonthCalCtrl :: IsDecadeView

Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue la plus décennie.

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue la plus décennie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) , qui est décrit dans le SDK Windows. Si ce message retourne MCMV_DECADE, cette méthode retourne TRUE.

##  <a name="ismonthview"></a>CMonthCalCtrl :: IsMonthView

Indique si la vue actuelle du contrôle calendrier du mois en cours est l’affichage du mois.

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue de mois ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) , qui est décrit dans le SDK Windows. Si ce message retourne MCMV_MONTH, cette méthode retourne TRUE.

##  <a name="isyearview"></a>CMonthCalCtrl :: IsYearView

Indique si la vue actuelle du contrôle calendrier du mois en cours est la vue Year.

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la vue actuelle est la vue Year ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) , qui est décrit dans le SDK Windows. Si ce message retourne MCMV_YEAR, cette méthode retourne TRUE.

##  <a name="setcalendarborder"></a>CMonthCalCtrl :: SetCalendarBorder

Définit la largeur de la bordure du contrôle calendrier du mois en cours.

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*cxyBorder*|dans Largeur de la bordure, en pixels.|

### <a name="remarks"></a>Notes

Si cette méthode est établie, la largeur de la bordure est définie sur le paramètre *cxyBorder* . Sinon, la largeur de la bordure est rétablie à la valeur par défaut spécifiée par le [thème](/windows/win32/Controls/visual-styles-overview)actuel, ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le message [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant affecte à la largeur de bordure du contrôle Month Calendar la valeur huit pixels. Utilisez la méthode [CMonthCalCtrl :: GetCalendarBorder](#getcalendarborder) pour déterminer si cette méthode a réussi.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>CMonthCalCtrl :: SetCalendarBorderDefault

Définit la largeur par défaut de la bordure du contrôle calendrier du mois en cours.

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Notes

La largeur de la bordure est définie sur la valeur par défaut spécifiée par le [thème](/windows/win32/Controls/visual-styles-overview)actuel, ou zéro si les thèmes ne sont pas utilisés.

Cette méthode envoie le message [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) , qui est décrit dans le SDK Windows.

##  <a name="setcalid"></a>CMonthCalCtrl :: SetCalID

Définit l’identificateur de calendrier pour le contrôle calendrier du mois en cours.

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*calid*|dans Une des constantes d' [identificateur de calendrier](/windows/win32/Intl/calendar-identifiers) .|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Un identificateur de calendrier spécifie un calendrier spécifique à une région, tel que les calendriers grégoriens (localisés), japonais ou Hijri. Utilisez la méthode `SetCalID` pour afficher un calendrier spécifié par le paramètre *calid* si les paramètres régionaux qui contiennent le calendrier sont installés sur votre ordinateur.

Cette méthode envoie le message [MCM_SETCALID](/windows/win32/Controls/mcm-setcalid) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle Month Calendar pour afficher le calendrier japonais de l’ère impérial. La méthode `SetCalID` ne fonctionne que si ce calendrier est installé sur votre ordinateur.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>CMonthCalCtrl :: SetCenturyView

Définit le contrôle calendrier du mois en cours pour afficher la vue du siècle.

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl :: SetCurrentView](#setcurrentview) pour définir la vue sur `MCMV_CENTURY`, qui représente la vue Century.

##  <a name="setcolor"></a>CMonthCalCtrl :: SetColor

Définit la couleur d’une zone spécifiée d’un contrôle Month Calendar.

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*nRegion*<br/>
Valeur entière spécifiant la couleur du calendrier mensuel à définir. Cette valeur peut être l’une des suivantes :

|Valeur|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|Couleur d’arrière-plan affichée entre les mois.|
|MCSC_MONTHBK|Couleur d’arrière-plan affichée dans le mois.|
|MCSC_TEXT|Couleur utilisée pour afficher le texte dans un mois.|
|MCSC_TITLEBK|Couleur d’arrière-plan affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|Couleur utilisée pour afficher le texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|Couleur utilisée pour afficher le texte de l’en-tête et du jour de fin. Les jours d’en-tête et de fin sont les jours des mois précédents et suivants qui apparaissent dans le calendrier actuel.|

*ref*<br/>
Valeur COLORREF pour le nouveau paramètre de couleur pour la partie spécifiée du contrôle Month Calendar.

### <a name="return-value"></a>Valeur de retour

Valeur COLORREF qui représente le paramètre de couleur précédent pour la partie spécifiée du contrôle Month Calendar, en cas de réussite. Sinon, ce message retourne-1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>CMonthCalCtrl :: SetCurrentView

Définit le contrôle calendrier du mois en cours pour afficher la vue spécifiée.

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwNewView*|dans L’une des valeurs suivantes, qui spécifie une vue mensuelle, annuelle, décennie ou Century.<br /><br /> MCMV_MONTH : vue mensuelle<br /><br /> MCMV_YEAR : vue annuelle<br /><br /> MCMV_DECADE : vue décennie<br /><br /> MCMV_CENTURY : affichage du siècle|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview) , qui est décrit dans le SDK Windows.

##  <a name="setcursel"></a>CMonthCalCtrl :: SetCurSel

Définit la date actuellement sélectionnée pour un contrôle Month Calendar.

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [ctime](../../atl-mfc-shared/reference/ctime-class.md) indiquant le contrôle de calendrier mensuel actuellement sélectionné.

*pDateTime*<br/>
Pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient la date à définir comme sélection actuelle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetCurSel`, vous pouvez spécifier une utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>CMonthCalCtrl :: SetDayState

Définit l’affichage pour les jours dans un contrôle Month Calendar.

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>Paramètres

*nMonths*<br/>
Valeur indiquant le nombre d’éléments dans le tableau vers lequel pointe *pStates* .

*pStates*<br/>
Pointeur vers un tableau de valeurs [MONTHDAYSTATE](/windows/win32/Controls/monthdaystate) qui définissent la façon dont le contrôle Month Calendar dessine chaque jour dans son affichage. Le type de données MONTHDAYSTATE est un champ de bits, où chaque bit (1 à 31) représente l’état d’un jour dans un mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>CMonthCalCtrl :: SetDecadeView

Définit le contrôle calendrier du mois en cours sur la vue décennie.

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl :: SetCurrentView](#setcurrentview) pour définir la vue sur `MCMV_DECADE`, qui représente la vue décennie.

##  <a name="setfirstdayofweek"></a>CMonthCalCtrl :: SetFirstDayOfWeek

Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>Paramètres

*iDay*<br/>
Valeur entière représentant le jour à définir comme premier jour de la semaine. Cette valeur doit être l’un des nombres de jours. Pour obtenir une description des numéros de jour, consultez [GetFirstDayOfWeek](#getfirstdayofweek) .

*lpnOld*<br/>
Pointeur vers un entier indiquant le premier jour de la semaine précédemment défini.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le premier jour de la semaine précédent est défini sur une valeur autre que celle de LOCALE_IFIRSTDAYOFWEEK, ce qui correspond au jour indiqué dans le paramètre du panneau de configuration. Dans le cas contraire, cette fonction retourne 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>CMonthCalCtrl :: SetMaxSelCount

Définit le nombre maximal de jours pouvant être sélectionnés dans un contrôle Month Calendar.

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>Paramètres

*nMax*<br/>
Valeur qui sera définie pour représenter le nombre maximal de jours sélectionnables.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>CMonthCalCtrl :: SetMonthDelta

Définit la vitesse de défilement pour un contrôle Month Calendar.

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>Paramètres

*iDelta*<br/>
Nombre de mois à définir comme taux de défilement du contrôle. Si cette valeur est égale à zéro, le delta du mois est rétabli à la valeur par défaut, qui est le nombre de mois affichés dans le contrôle.

### <a name="return-value"></a>Valeur de retour

Taux de défilement précédent. Si la vitesse de défilement n’a pas été définie précédemment, la valeur de retour est 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)de message Win32, comme décrit dans le SDK Windows.

##  <a name="setmonthview"></a>CMonthCalCtrl :: SetMonthView

Définit le contrôle calendrier du mois en cours pour afficher l’affichage du mois.

```
BOOL SetMonthView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl :: SetCurrentView](#setcurrentview) pour définir la vue sur MCMV_MONTH, qui représente l’affichage mois.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisée pour accéder par programmation au contrôle Month Calendar. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle Month Calendar pour afficher les affichages mois, année, décennie et siècle.

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>CMonthCalCtrl :: SetRange

Définit les dates minimale et maximale autorisées pour un contrôle Month Calendar.

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
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus basse de la plage.

*pMaxRange*<br/>
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure `SYSTEMTIME` contenant la date à la fin la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetRange`, vous pouvez spécifier l’utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl :: GetRange](#getrange).

##  <a name="setselrange"></a>CMonthCalCtrl :: SetSelRange

Définit la sélection d’un contrôle Month Calendar sur une plage de dates donnée.

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
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant la date à la fin la plus basse de la plage.

*pMaxRange*<br/>
Pointeur vers un objet `COleDateTime`, un objet `CTime` ou une structure `SYSTEMTIME` contenant la date à la fin la plus élevée de la plage.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetSelRange`, vous pouvez spécifier l’utilisation de `COleDateTime`, une utilisation de `CTime` ou une utilisation de structure de `SYSTEMTIME`.

##  <a name="settoday"></a>CMonthCalCtrl :: SetToday

Définit le contrôle calendrier pour le jour actuel.

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>Paramètres

*refDateTime*<br/>
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient la date actuelle.

*pDateTime*<br/>
Dans la deuxième version, pointeur vers un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant les informations de date actuelles. Dans la troisième version, pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient les informations de date actuelles.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CMonthCalCtrl :: GetToday](#gettoday).

##  <a name="setyearview"></a>CMonthCalCtrl :: SetYearView

Définit le contrôle calendrier du mois en cours sur l’affichage année.

```
BOOL SetYearView();
```

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode utilise la méthode [CMonthCalCtrl :: SetCurrentView](#setcurrentview) pour définir la vue sur MCMV_YEAR, qui représente la vue annuelle.

##  <a name="sizeminreq"></a>CMonthCalCtrl :: SizeMinReq

Affiche le contrôle calendrier du mois à la taille minimale qui affiche un mois.

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRepaint*<br/>
Spécifie si le contrôle doit être repeint. Par défaut, TRUE. Si la valeur est FALSe, aucun redessin ne se produit.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contrôle Month Calendar est dimensionné à sa valeur minimale ; Sinon, 0.

### <a name="remarks"></a>Notes

L’appel de `SizeMinReq` affiche le contrôle de calendrier mensuel entier pour le calendrier d’un mois.

##  <a name="sizerecttomin"></a>CMonthCalCtrl :: SizeRectToMin

Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*lpRect*|dans Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui définit un rectangle qui contient le nombre souhaité de calendriers.|

### <a name="return-value"></a>Valeur de retour

Pointeur vers une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui définit un rectangle dont la taille est inférieure ou égale au rectangle défini par le paramètre *lpRect* .

### <a name="remarks"></a>Notes

Cette méthode calcule le nombre de calendriers pouvant tenir dans le rectangle spécifié par le paramètre *lpRect* , puis retourne le plus petit rectangle qui peut contenir ce nombre de calendriers. En effet, cette méthode réduit le rectangle spécifié pour qu’il corresponde exactement au nombre souhaité de calendriers.

Cette méthode envoie le message [MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin) , qui est décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl, classe](../../mfc/reference/cdatetimectrl-class.md)
