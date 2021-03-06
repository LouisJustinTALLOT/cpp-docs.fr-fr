---
description: 'En savoir plus sur : CDateTimeCtrl, classe'
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
ms.openlocfilehash: cfed57d74e16f8433a5199ca912379b90a4f48cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247929"
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
|[CDateTimeCtrl :: CDateTimeCtrl](#cdatetimectrl)|Construit un objet `CDateTimeCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDateTimeCtrl :: CloseMonthCal](#closemonthcal)|Ferme le contrôle de sélecteur de date et d’heure actuel.|
|[CDateTimeCtrl :: Create](#create)|Crée le contrôle de sélecteur de date et d’heure et l’attache à l' `CDateTimeCtrl` objet.|
|[CDateTimeCtrl :: GetDateTimePickerInfo](#getdatetimepickerinfo)|Récupère des informations sur le contrôle de sélecteur de date et d’heure actuel.|
|[CDateTimeCtrl :: GetIdealSize](#getidealsize)|Retourne la taille idéale du contrôle de sélecteur de dates et d’heures qui est nécessaire pour afficher la date ou l’heure actuelle.|
|[CDateTimeCtrl :: GetMonthCalColor](#getmonthcalcolor)|Récupère la couleur d’une partie donnée du calendrier du mois dans le contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl :: GetMonthCalCtrl](#getmonthcalctrl)|Récupère l' `CMonthCalCtrl` objet associé au contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl :: GetMonthCalFont](#getmonthcalfont)|Récupère la police actuellement utilisée par le contrôle calendrier mensuel enfant du contrôle date et heure.|
|[CDateTimeCtrl :: GetMonthCalStyle](#getmonthcalstyle)|Obtient le style du contrôle de sélecteur de date et d’heure actuel.|
|[CDateTimeCtrl :: GetRange](#getrange)|Récupère les heures système actuelles minimale et maximale autorisées pour un contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl :: GetTime](#gettime)|Récupère l’heure actuellement sélectionnée dans un contrôle de sélecteur de dates et d’heures et la place dans une `SYSTEMTIME` structure spécifiée.|
|[CDateTimeCtrl :: SetFormat](#setformat)|Définit l’affichage d’un contrôle de sélecteur de date et d’heure conformément à une chaîne de format donnée.|
|[CDateTimeCtrl :: SetMonthCalColor](#setmonthcalcolor)|Définit la couleur d’une partie donnée du calendrier du mois dans un contrôle de sélecteur de dates et d’heures.|
|[CDateTimeCtrl :: SetMonthCalFont](#setmonthcalfont)|Définit la police que le contrôle de calendrier mensuel enfant du contrôle date et heure doit utiliser.|
|[CDateTimeCtrl :: SetMonthCalStyle](#setmonthcalstyle)|Définit le style du contrôle de sélecteur de date et d’heure actuel.|
|[CDateTimeCtrl :: SetRange](#setrange)|Définit les heures système minimale et maximale autorisées pour un contrôle de sélecteur de date et d’heure.|
|[CDateTimeCtrl :: SetTime](#settime)|Définit l’heure dans un contrôle de sélecteur de date et d’heure.|

## <a name="remarks"></a>Notes

Le contrôle de sélecteur de date et heure (contrôle de PAO) fournit une interface simple permettant d’échanger des informations de date et d’heure avec un utilisateur. Cette interface contient des champs, chacun d’entre eux affichant une partie des informations de date et d’heure stockées dans le contrôle. L’utilisateur peut modifier les informations stockées dans le contrôle en modifiant le contenu de la chaîne dans un champ donné. L’utilisateur peut passer d’un champ à un champ à l’aide de la souris ou du clavier.

Vous pouvez personnaliser le contrôle de sélecteur de date et d’heure en appliquant divers styles à l’objet lors de sa création. Pour plus d’informations sur les styles spécifiques au contrôle de sélecteur de date et d’heure, consultez [styles de contrôle de sélecteur](/windows/win32/Controls/date-and-time-picker-control-styles) de dates et d’heures dans le SDK Windows. Vous pouvez définir le format d’affichage du contrôle de PAO à l’aide de styles de format. Ces styles de format sont décrits sous « styles de format » dans les [styles de contrôle de sélecteur de date et d’heure](/windows/win32/Controls/date-and-time-picker-control-styles)de la rubrique SDK Windows.

Le contrôle de sélecteur de date et d’heure utilise également des notifications et des rappels, qui sont décrits dans [utilisation de CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDTCTL. h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a> CDateTimeCtrl :: CDateTimeCtrl

Construit un objet `CDateTimeCtrl`.

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a> CDateTimeCtrl :: CloseMonthCal

Ferme le contrôle de sélecteur de date et d’heure actuel.

```cpp
void CloseMonthCal() const;
```

### <a name="remarks"></a>Notes

Cette méthode envoie le message [DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder par programmation au contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant ferme le calendrier déroulant pour le contrôle de sélecteur de date et d’heure actuel.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a> CDateTimeCtrl :: Create

Crée le contrôle de sélecteur de date et d’heure et l’attache à l' `CDateTimeCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie la combinaison de styles de contrôle de date et d’heure. Pour plus d’informations sur les styles de sélecteur de date et d’heure, consultez [styles de contrôle de sélecteur de date et heure](/windows/win32/Controls/date-and-time-picker-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) , qui est la position et la taille du contrôle de sélecteur de date et d’heure.

*pParentWnd*<br/>
Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle de sélecteur de date et d’heure. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID de contrôle du contrôle de sélecteur de date et d’heure.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si la création a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

##### <a name="to-create-a-date-and-time-picker-control"></a>Pour créer un contrôle de sélecteur de date et d’heure

1. Appelez [CDateTimeCtrl](#cdatetimectrl) pour construire un `CDateTimeCtrl` objet.

1. Appelez cette fonction membre, qui crée le contrôle de sélecteur de date et d’heure Windows et l’attache à l' `CDateTimeCtrl` objet.

Lorsque vous appelez `Create` , les contrôles communs sont initialisés.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a> CDateTimeCtrl :: GetDateTimePickerInfo

Récupère des informations sur le contrôle de sélecteur de date et d’heure actuel.

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>Paramètres

*pDateTimePickerInfo*\
à Pointeur vers une structure [DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo) qui reçoit une description du contrôle de sélecteur de date et d’heure actuel. L’appelant est chargé d’allouer cette structure. Toutefois, cette méthode initialise le membre *cbSize* de la structure.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder par programmation au contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant indique s’il récupère avec succès des informations sur le contrôle de sélecteur de date et d’heure actuel.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a> CDateTimeCtrl :: GetMonthCalColor

Récupère la couleur d’une partie donnée du calendrier du mois dans le contrôle de sélecteur de date et d’heure.

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>Paramètres

*iColor*<br/>
**`int`** Valeur qui spécifie la zone de couleur du calendrier du mois à récupérer. Pour obtenir la liste des valeurs, consultez le paramètre *iColor* pour [SetMonthCalColor](#setmonthcalcolor).

### <a name="return-value"></a>Valeur renvoyée

Valeur COLORREF qui représente le paramètre de couleur de la partie spécifiée du contrôle Month Calendar en cas de réussite. La fonction retourne-1 en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a> CDateTimeCtrl :: GetMonthCalCtrl

Récupère l' `CMonthCalCtrl` objet associé au contrôle de sélecteur de date et d’heure.

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) , ou null en cas d’échec ou si la fenêtre n’est pas visible.

### <a name="remarks"></a>Notes

Les contrôles de sélecteur de date et d’heure créent un contrôle Month Calendar enfant lorsque l’utilisateur clique sur la flèche déroulante. Lorsque l' `CMonthCalCtrl` objet n’est plus nécessaire, il est détruit, de sorte que votre application ne doit pas compter sur le stockage de l’objet représentant le calendrier mensuel du mois enfant du contrôle Date Time Picker.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a> CDateTimeCtrl :: GetMonthCalFont

Obtient la police actuellement utilisée par le contrôle Month Calendar du contrôle date et Time Picker.

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CFont](../../mfc/reference/cfont-class.md) , ou null en cas d’échec.

### <a name="remarks"></a>Notes

L' `CFont` objet vers lequel pointe la valeur de retour est un objet temporaire et il est détruit pendant le temps de traitement inactif suivant.

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a> CDateTimeCtrl :: GetMonthCalStyle

Obtient le style du contrôle calendrier du mois déroulant associé au contrôle de sélecteur de date et d’heure actuel.

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>Valeur renvoyée

Style du contrôle de calendrier du mois de la liste déroulante, qui est une combinaison au niveau du bit (ou) des styles de contrôle de sélecteur de date et d’heure. Pour plus d’informations, consultez [styles de contrôle de calendrier mensuel](/windows/win32/Controls/month-calendar-control-styles).

### <a name="remarks"></a>Notes

Cette méthode envoie le message [DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle) , qui est décrit dans le SDK Windows.

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a> CDateTimeCtrl :: GetRange

Récupère les heures système actuelles minimale et maximale autorisées pour un contrôle de sélecteur de date et d’heure.

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
Pointeur vers un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant la plus ancienne heure autorisée dans l' `CDateTimeCtrl` objet.

*pMaxRange*<br/>
Pointeur vers un `COleDateTime` objet ou un `CTime` objet contenant l’heure la plus récente autorisée dans l' `CDateTimeCtrl` objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur DWORD contenant des indicateurs qui indiquent les plages définies. If

`return value & GDTR_MAX` == 0

le deuxième paramètre est alors valide. De même, si

`return value & GDTR_MIN` == 0

le premier paramètre est alors valide.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation de MFC, vous pouvez spécifier `COleDateTime` des `CTime` utilisations ou.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a> CDateTimeCtrl :: GetTime

Récupère l’heure actuellement sélectionnée dans un contrôle de sélecteur de dates et d’heures et la place dans une `SYSTEMTIME` structure spécifiée.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Paramètres

*le plus chronométré*<br/>
Dans la première version, référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations d’heure système. Dans la deuxième version, référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations d’heure système.

*pTimeDest*<br/>
Pointeur vers la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations d’heure système. Ne doit pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

Dans la première version, différente de zéro si l’heure est correctement écrite dans l' `COleDateTime` objet ; sinon, 0. Dans la deuxième et la troisième version, il s’agit d’une valeur DWORD égale au membre *dwFlag* défini dans la structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) . Pour plus d’informations, consultez la section **Notes** ci-dessous.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `GetTime` , vous pouvez utiliser `COleDateTime` des `CTime` classes ou, ou vous pouvez utiliser une `SYSTEMTIME` structure pour stocker les informations d’heure.

La valeur de retour DWORD dans la deuxième et la troisième version ci-dessus indique si le contrôle de sélecteur de date et d’heure est défini sur l’État « aucune date », comme indiqué dans le membre de structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) *dwFlags*. Si la valeur retournée est égale à GDT_NONE, le contrôle a la valeur « no date » et utilise le style DTS_SHOWNONE. Si la valeur retournée est égale à GDT_VALID, l’heure système est stockée dans l’emplacement de destination.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a> CDateTimeCtrl :: GetIdealSize

Retourne la taille idéale du contrôle de sélecteur de dates et d’heures qui est nécessaire pour afficher la date ou l’heure actuelle.

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>Paramètres

*psize*\
à Pointeur vers une structure de [taille](/windows/win32/api/windef/ns-windef-size) qui contient la taille idéale pour le contrôle.

### <a name="return-value"></a>Valeur renvoyée

La valeur de retour est toujours TRUE.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder par programmation au contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant récupère la taille idéale pour afficher le contrôle de sélecteur de date et d’heure.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a> CDateTimeCtrl :: SetFormat

Définit l’affichage d’un contrôle de sélecteur de date et d’heure conformément à une chaîne de format donnée.

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>Paramètres

*pstrFormat*<br/>
Pointeur vers une chaîne de format se terminant par zéro qui définit l’affichage souhaité. Si ce paramètre a la valeur NULL, le contrôle est réinitialisé à la chaîne de format par défaut pour le style actuel.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

> [!NOTE]
> L’entrée utilisateur ne détermine pas la réussite ou l’échec de cet appel.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a> CDateTimeCtrl :: SetMonthCalColor

Définit la couleur d’une partie donnée du calendrier du mois dans un contrôle de sélecteur de dates et d’heures.

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>Paramètres

*iColor*<br/>
**`int`** valeur spécifiant la zone du contrôle Month Calendar à définir. Cette valeur peut être l’une des suivantes :

|Valeur|Signification|
|-----------|-------------|
|MCSC_BACKGROUND|Définissez la couleur d’arrière-plan affichée entre les mois.|
|MCSC_MONTHBK|Définissez la couleur d’arrière-plan affichée dans un mois.|
|MCSC_TEXT|Définissez la couleur utilisée pour afficher le texte dans un mois.|
|MCSC_TITLEBK|Définissez la couleur d’arrière-plan affichée dans le titre du calendrier.|
|MCSC_TITLETEXT|Définissez la couleur utilisée pour afficher le texte dans le titre du calendrier.|
|MCSC_TRAILINGTEXT|Définissez la couleur utilisée pour afficher le texte de l’en-tête et du jour de fin. Les jours d’en-tête et de fin sont les jours des mois précédents et suivants qui apparaissent dans le calendrier actuel.|

*ref*<br/>
Valeur COLORREF représentant la couleur qui sera définie pour la zone spécifiée du calendrier du mois.

### <a name="return-value"></a>Valeur renvoyée

Valeur COLORREF qui représente le paramètre de couleur précédent pour la partie spécifiée du contrôle Month Calendar en cas de réussite. Dans le cas contraire, le message retourne-1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CDateTimeCtrl :: GetMonthCalColor](#getmonthcalcolor).

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a> CDateTimeCtrl :: SetMonthCalFont

Définit la police que le contrôle de calendrier mensuel enfant du contrôle date et heure doit utiliser.

```cpp
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*hFont*<br/>
Handle de la police qui sera définie.

*bRedraw*<br/>
Spécifie si le contrôle doit être redessiné immédiatement lors de la définition de la police. Si ce paramètre a la valeur TRUE, le contrôle se redessine lui-même.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)de message Win32, comme décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> Si vous utilisez ce code, vous souhaiterez créer un membre de votre `CDialog` classe dérivée de, appelé *m_MonthFont* de type `CFont` .

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a> CDateTimeCtrl :: SetMonthCalStyle

Définit le style du contrôle de calendrier mensuel déroulant associé au contrôle de sélecteur de date et d’heure actuel.

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*\
dans Nouveau style de contrôle Month Calendar, qui est une combinaison au niveau du bit (OR) des styles du contrôle Month Calendar. Pour plus d’informations, consultez [styles de contrôle de calendrier mensuel](/windows/win32/Controls/month-calendar-control-styles).

### <a name="return-value"></a>Valeur renvoyée

Le style précédent du contrôle de calendrier mensuel déroulant.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle) , qui est décrit dans le SDK Windows.

### <a name="example"></a>Exemple

L’exemple de code suivant définit la variable, *m_dateTimeCtrl*, qui est utilisée pour accéder par programmation au contrôle de sélecteur de date et d’heure. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant définit le contrôle de sélecteur de date et d’heure pour afficher les numéros de semaine, les noms abrégés des jours de la semaine et aucun indicateur Today.

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a> CDateTimeCtrl :: SetRange

Définit les heures système minimale et maximale autorisées pour un contrôle de sélecteur de date et d’heure.

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
Pointeur vers un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant la plus ancienne heure autorisée dans l' `CDateTimeCtrl` objet.

*pMaxRange*<br/>
Pointeur vers un `COleDateTime` objet ou un `CTime` objet contenant l’heure la plus récente autorisée dans l' `CDateTimeCtrl` objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation de MFC, vous pouvez spécifier `COleDateTime` des `CTime` utilisations ou. Si l' `COleDateTime` objet a un État null, la plage sera supprimée. Si le `CTime` pointeur ou le `COleDateTime` pointeur a la valeur null, la plage sera supprimée.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CDateTimeCtrl :: GetRange](#getrange).

## <a name="cdatetimectrlsettime"></a><a name="settime"></a> CDateTimeCtrl :: SetTime

Définit l’heure dans un contrôle de sélecteur de date et d’heure.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>Paramètres

*timeNew*<br/>
Référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) contenant le auquel le contrôle sera défini.

*pTimeNew*<br/>
Dans la deuxième version ci-dessus, pointeur vers un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) contenant l’heure à laquelle le contrôle sera défini. Dans la troisième version ci-dessus, pointeur vers une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) contenant l’heure à laquelle le contrôle sera défini.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)de message Win32, comme décrit dans le SDK Windows. Dans l’implémentation MFC de `SetTime` , vous pouvez utiliser les `COleDateTime` `CTime` classes ou, ou vous pouvez utiliser une `SYSTEMTIME` structure pour définir les informations d’heure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl (classe)](../../mfc/reference/cmonthcalctrl-class.md)
