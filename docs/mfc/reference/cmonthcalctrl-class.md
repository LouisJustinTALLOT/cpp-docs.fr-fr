---
title: CMonthCalCtrl (classe) | Documents Microsoft
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
ms.openlocfilehash: 45e0499297c814e4a214962bc2f51404960a8c38
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039217"
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
|[CMonthCalCtrl::Create](#create)|Crée un contrôle month calendar et l’attache à le `CMonthCalCtrl` objet.|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Récupère la largeur de la bordure du contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Récupère le nombre de calendriers affichés dans le contrôle calendrier du mois en cours.|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Récupère des informations à propos du contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::GetCalID](#getcalid)|Récupère l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::GetColor](#getcolor)|Obtient la couleur d’une zone spécifiée d’un contrôle month calendar.|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Récupère la vue actuellement affichée par le contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|Récupère l’heure système, comme indiqué par la date actuellement sélectionnée.|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Récupère le nombre maximal actuel de jours qui peuvent être sélectionnées dans un contrôle month calendar.|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Récupère la largeur maximale de la chaîne « Aujourd'hui » pour le contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Récupère la taille minimale nécessaire pour afficher un mois complet dans un contrôle month calendar.|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Récupère la vitesse de défilement d’un contrôle month calendar.|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Récupère les informations représentant les limites de haute et bas d’affichage d’un contrôle de calendrier mois de date.|  
|[CMonthCalCtrl::GetRange](#getrange)|Récupère les dates de minimales et maximales actuelles définies dans un contrôle month calendar.|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|Récupère les informations de date représentant les limites supérieures et inférieures de la plage de dates actuellement sélectionnée par l’utilisateur.|  
|[CMonthCalCtrl::GetToday](#gettoday)|Récupère les informations de date pour la date spécifiée en tant que « aujourd'hui » pour un contrôle month calendar.|  
|[CMonthCalCtrl::HitTest](#hittest)|Détermine quelle section d’un contrôle month calendar est à un moment donné sur l’écran.|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue appartient au siècle.|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue des dix dernières années.|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue du mois.|  
|[CMonthCalCtrl::IsYearView](#isyearview)|Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue de l’année.|  
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Définit la largeur de la bordure du contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Définit la largeur par défaut de la bordure du contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::SetCalID](#setcalid)|Définit l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.|  
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Définit le contrôle de calendrier mois en cours pour afficher la vue appartient au siècle.|  
|[CMonthCalCtrl::SetColor](#setcolor)|Définit la couleur d’une zone spécifiée d’un contrôle month calendar.|  
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Définit le contrôle de calendrier mois en cours pour afficher la vue spécifiée.|  
|[CMonthCalCtrl::SetCurSel](#setcursel)|Définit la date actuellement sélectionnée pour un contrôle month calendar.|  
|[CMonthCalCtrl::SetDayState](#setdaystate)|Définit l’affichage des jours dans un contrôle month calendar.|  
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Définit le calendrier du mois en cours contrôle à la vue des dix dernières années.|  
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.|  
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Définit le nombre maximal de jours pouvant être sélectionnés dans un contrôle month calendar.|  
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Définit la vitesse de défilement d’un contrôle month calendar.|  
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Définit le contrôle de calendrier mois en cours pour afficher la vue du mois.|  
|[CMonthCalCtrl::SetRange](#setrange)|Définit les valeurs minimale et le nombre maximal autorisé de dates pour un contrôle month calendar.|  
|[CMonthCalCtrl::SetSelRange](#setselrange)|Définit la sélection d’un calendrier du mois contrôle à une plage de dates donnée.|  
|[CMonthCalCtrl::SetToday](#settoday)|Définit le contrôle de calendrier pour le jour actuel.|  
|[CMonthCalCtrl::SetYearView](#setyearview)|Définit le calendrier du mois en cours contrôle en mode année.|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Repeint le calendrier du mois contrôle à sa taille minimale, un mois.|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.|  
  
## <a name="remarks"></a>Notes  
 Le contrôle month calendar fournit à l’utilisateur avec une interface de calendrier simple, à partir de laquelle l’utilisateur peut sélectionner une date. L’utilisateur peut modifier l’affichage par :  
  
-   Le défilement vers le haut et vers l’avant, à partir du mois pour le mois.  
  
-   En cliquant sur le texte de la date du jour pour afficher la date du jour (si le **MCS_NOTODAY** style n’est pas utilisé).  
  
-   Sélection d’un mois ou une année dans un menu déroulant.  
  
 Vous pouvez personnaliser le mois contrôle calendar en appliquant différents styles à l’objet lors de sa création. Ces styles sont décrites dans [Styles de contrôle Month Calendar](http://msdn.microsoft.com/library/windows/desktop/bb760919) dans le Kit de développement logiciel Windows.  
  
 Le contrôle month calendar peut afficher plusieurs mois, et il peut indiquer les jours spéciaux (tels que les jours fériés) en caractères gras la date.  
  
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
 Vous devez appeler **créer** après avoir construit l’objet.  
  
##  <a name="create"></a>  CMonthCalCtrl::Create  
 Crée un contrôle month calendar et l’attache à le `CMonthCalCtrl` objet.  
  
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
 *dwStyle*  
 Spécifie la combinaison de styles de Windows appliqués au contrôle month calendar. Consultez [Styles de contrôle Month Calendar](http://msdn.microsoft.com/library/windows/desktop/bb760919) dans le SDK Windows pour plus d’informations sur les styles.  
  
 *Rect*  
 Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure. Contient la position et la taille du contrôle month calendar.  
  
 *pt*  
 Une référence à un [POINT](http://msdn.microsoft.com/library/windows/desktop/dd162805) structure qui identifie l’emplacement du contrôle month calendar.  
  
 *pParentWnd*  
 Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle month calendar. Il ne doit pas être **NULL**.  
  
 *nID*  
 Spécifie l’ID de contrôle. du contrôle month calendar  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’initialisation a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Créer un mois du calendrier contrôle en deux étapes :  
  
1.  Appelez [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) pour construire un `CMonthCalCtrl` objet.  
  
2.  Appelez cette fonction membre, ce qui crée un contrôle month calendar et l’attache à le `CMonthCalCtrl` objet.  
  
 Lorsque vous appelez `Create`, les contrôles communs sont initialisés. La version de `Create` vous appel détermine la façon dont elle est dimensionnée :  
  
-   Pour que MFC automatiquement la taille du contrôle à un mois, appelez le remplacement qui utilise le *pt* paramètre.  
  
-   Pour redimensionner le contrôle vous-même, appelez le remplacement de cette fonction qui utilise le *rect* paramètre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder  
 Récupère la largeur de la bordure du contrôle de calendrier du mois en cours.  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur de la bordure du contrôle, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount  
 Récupère le nombre de calendriers affichés dans le contrôle calendrier du mois en cours.  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de calendriers actuellement affichée dans le contrôle month calendar. Le nombre maximal autorisé de calendriers est 12.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo  
 Récupère des informations à propos du contrôle de calendrier du mois en cours.  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[out] *pmcGridInfo*|Pointeur vers un [MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925) structure qui reçoit des informations à propos du contrôle de calendrier du mois en cours. L’appelant est chargé d’allouer et de l’initialisation de cette structure.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Exemple  
 Le code suivant exemple utilise le `GetCalendarGridInfo` pour récupérer la date du calendrier affichant le contrôle de calendrier du mois en cours.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID  
 Récupère l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Parmi les [identificateur de calendrier](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.  
  
### <a name="remarks"></a>Notes  
 Un identificateur de calendrier indique un calendrier spécifique à la région, tels que le calendrier grégorien (localisé), japonais ou Hijri calendriers. Votre application peut utiliser un identificateur de calendrier a différents langue prend en charge des fonctions.  
  
 Cette méthode envoie le [MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor  
 Récupère la couleur d’une zone du mois du calendrier contrôle spécifié par *nRegion*.  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nRegion*  
 La région du contrôle month calendar à partir de laquelle la couleur est récupérée. Pour obtenir la liste de valeurs, consultez le *nRegion* paramètre de [SetColor](#setcolor).  
  
### <a name="return-value"></a>Valeur de retour  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui spécifie la couleur associée à la partie du contrôle month calendar, en cas de réussite. Sinon, cette fonction membre retourne -1.  
  
##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView  
 Récupère la vue actuellement affichée par le contrôle de calendrier du mois en cours.  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’affichage actuel, qui est indiqué par une des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|`MCMV_MONTH`|Affichage mensuel|  
|`MCMV_YEAR`|Vue annuel|  
|`MCMV_DECADE`|Affichage de dix ans|  
|`MCMV_CENTURY`|Affichage de siècle|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
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
 *refDateTime*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet ou un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet. Reçoit l’heure actuelle.  
  
 *pDateTime*  
 Un pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui recevront les informations de date d’actuellement sélectionné. Ce paramètre doit être une adresse valide et ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; otherwize 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957), comme décrit dans le Kit de développement logiciel Windows.  
  
> [!NOTE]
>  Cette fonction membre échoue si le style **MCS_MULTISELECT** est défini.  
  
 Dans l’implémentation MFC de `GetCurSel`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek  
 Obtient le premier jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pbLocal*  
 Un pointeur vers un **BOOL** valeur. Si la valeur est différente de zéro, le paramètre du contrôle ne correspond pas le paramètre dans le panneau de configuration.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur entière qui représente le premier jour de la semaine. Consultez **remarques** pour plus d’informations sur la signification de ces nombres entiers.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958), comme décrit dans le Kit de développement logiciel Windows. Les jours de la semaine sont représentées en tant qu’entiers, comme suit.  
  
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
 Une valeur entière qui représente le nombre total de jours qui peuvent être sélectionnées pour le contrôle.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960), comme décrit dans le Kit de développement logiciel Windows. Utilisez cette fonction membre pour les contrôles avec le **MCS_MULTISELECT** set de style.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).  
  
##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth  
 Récupère la largeur maximale de la chaîne « Aujourd'hui » pour le contrôle de calendrier du mois en cours.  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur de la chaîne « Aujourd'hui », en pixels.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre la `GetMaxTodayWidth` (méthode).  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>Notes  
 L’utilisateur peut revenir à la date actuelle en cliquant sur la chaîne « Aujourd'hui », qui s’affiche en bas du contrôle month calendar. La chaîne « Aujourd'hui » inclut le texte d’étiquette et le texte de la date.  
  
 Cette méthode envoie le [MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect  
 Récupère la taille minimale nécessaire pour afficher un mois complet dans un contrôle month calendar.  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pRect*  
 Un pointeur vers un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui recevront les informations de rectangle englobant. Ce paramètre doit être une adresse valide et ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la réussite, cette fonction membre retourne différente de zéro et `lpRect` reçoit les informations applicables. En cas d’échec, la fonction membre retourne 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta  
 Récupère la vitesse de défilement d’un contrôle month calendar.  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La vitesse de défilement pour le contrôle month calendar. La vitesse de défilement est le nombre de mois que le contrôle passe de son affichage lorsque l’utilisateur clique sur un bouton de défilement en une seule fois.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange  
 Récupère les informations représentant les limites de haute et bas d’affichage d’un contrôle de calendrier mois de date.  
  
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
 *refMinRange*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la date minimale autorisée.  
  
 *refMaxRange*  
 Une référence à un `COleDateTime` ou `CTime` objet contenant la date maximale autorisée.  
  
 *pMinRange*  
 Un pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.  
  
 *pMaxRange*  
 Un pointeur vers un `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.  
  
 *dwFlags*  
 Valeur qui spécifie l’étendue de la plage de la limite doit être récupéré. Cette valeur doit être une des opérations suivantes.  
  
|Value|Signification|  
|-----------|-------------|  
|GMR_DAYSTATE|Inclure les précédents et de fin de mois à compter de la plage visible que partiellement affichées.|  
|GMR_VISIBLE|Inclure uniquement ces mois entièrement affichés.|  
  
### <a name="return-value"></a>Valeur de retour  
 Entier qui représente la plage, en mois, couvertes par les deux limites indiquées par *refMinRange* et *refMaxRange* dans les versions de première et deuxième, ou *pMinRange* et *pMaxRange* dans la troisième version.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `GetMonthRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMonthCalCtrl::SetDayState](#setdaystate).  
  
##  <a name="getrange"></a>  CMonthCalCtrl::GetRange  
 Récupère les dates de minimales et maximales actuelles définies dans un contrôle month calendar.  
  
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
 *pMinRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.  
  
 *pMaxRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus élevée de la plage.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `DWORD` qui peut être égal à zéro (aucune limite n’est définis) ou une combinaison des valeurs suivantes qui spécifient les informations de limite.  
  
|Value|Signification|  
|-----------|-------------|  
|GDTR_MAX|Une limite maximale est définie pour le contrôle ; *pMaxRange* est valide et contient les informations de date applicable.|  
|GDTR_MIN|Une limite minimale est définie pour le contrôle ; *pMinRange* est valide et contient les informations de date applicable.|  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `GetRange`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
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
 *refMinRange*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant la date minimale autorisée.  
  
 *refMaxRange*  
 Une référence à un `COleDateTime` ou `CTime` objet contenant la date maximale autorisée.  
  
 *pMinRange*  
 Un pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.  
  
 *pMaxRange*  
 Un pointeur vers un `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985), comme décrit dans le Kit de développement logiciel Windows. `GetSelRange` échoue si appliqué à un contrôle month calendar qui n’utilise pas le **MCS_MULTISELECT** style.  
  
 Dans l’implémentation MFC de `GetSelRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday  
 Récupère les informations de date pour la date spécifiée en tant que « aujourd'hui » pour un contrôle month calendar.  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *refDateTime*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet indiquant le jour actuel.  
  
 *pDateTime*  
 Un pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui recevront les informations de date. Ce paramètre doit être une adresse valide et ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `GetToday`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="hittest"></a>  CMonthCalCtrl::HitTest  
 Détermine le contrôle calendrier du mois, si elle existe, est à la position spécifiée.  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>Paramètres  
 *pMCHitTest*  
 Un pointeur vers un [MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927) points de la structure qui contient un test de positionnement pour le contrôle month calendar.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `DWORD`. Égal à la **uHit** membre de la **MCHITTESTINFO** structure.  
  
### <a name="remarks"></a>Notes  
 `HitTest` utilise le **MCHITTESTINFO** structure qui contient des informations sur le test de positionnement.  
  
##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView  
 Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue appartient au siècle.  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’affichage actuel est le siècle ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) message, ce qui est décrit dans le Kit de développement logiciel Windows. Si que message retourne `MCMV_CENTURY`, cette méthode retourne `true`.  
  
##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView  
 Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue des dix dernières années.  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la vue actuelle est la vue de dix ans ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) message, ce qui est décrit dans le Kit de développement logiciel Windows. Si que message retourne `MCMV_DECADE`, cette méthode retourne `true`.  
  
##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView  
 Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue du mois.  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la vue actuelle est la vue du mois ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) message, ce qui est décrit dans le Kit de développement logiciel Windows. Si que message retourne `MCMV_MONTH`, cette méthode retourne `true`.  
  
##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView  
 Indique si l’affichage actuel du contrôle de calendrier mois en cours est la vue de l’année.  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la vue actuelle est la vue de l’année ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) message, ce qui est décrit dans le Kit de développement logiciel Windows. Si que message retourne `MCMV_YEAR`, cette méthode retourne `true`.  
  
##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder  
 Définit la largeur de la bordure du contrôle de calendrier du mois en cours.  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *cxyBorder*|La largeur de la bordure, en pixels.|  
  
### <a name="remarks"></a>Notes  
 Si cette méthode réussit, la largeur de bordure est définie sur le *cxyBorder* paramètre. Dans le cas contraire, la largeur de bordure est réinitialisée à la valeur par défaut qui est spécifiée par l’actuel [thème](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), ou zéro si les thèmes ne sont pas utilisés.  
  
 Cette méthode envoie le [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Exemple  
 Le code exemple suivant définit la largeur de bordure du calendrier du mois le contrôle à huit pixels. Utilisez le [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) méthode pour déterminer si cette méthode a réussi.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault  
 Définit la largeur par défaut de la bordure du contrôle de calendrier du mois en cours.  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>Notes  
 La largeur de bordure est définie sur la valeur par défaut spécifiée par l’actuel [thème](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), ou zéro si les thèmes ne sont pas utilisés.  
  
 Cette méthode envoie le [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID  
 Définit l’identificateur de calendrier pour le contrôle de calendrier du mois en cours.  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *calid*|Parmi les [identificateur de calendrier](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Un identificateur de calendrier spécifie un calendrier spécifique à la région, tels que le calendrier grégorien (localisé), japonais ou Hijri calendriers. Utilisez le `SetCalID` méthode pour afficher un calendrier spécifié par le *calid* paramètre, si les paramètres régionaux qui contient le calendrier sont installé sur votre ordinateur.  
  
 Cette méthode envoie le [MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit le contrôle month calendar pour afficher le Calendrier impérial japonais. Le `SetCalID` méthode réussit uniquement si ce calendrier est installé sur votre ordinateur.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView  
 Définit le contrôle de calendrier mois en cours pour afficher la vue appartient au siècle.  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode utilise le [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue `MCMV_CENTURY`, qui représente la vue appartient au siècle.  
  
##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor  
 Définit la couleur d’une zone spécifiée d’un contrôle month calendar.  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Paramètres  
 *nRegion*  
 Valeur entière spécifiant la couleur de calendrier de mois à définir. Cette valeur peut être une des opérations suivantes.  
  
|Value|Signification|  
|-----------|-------------|  
|MCSC_BACKGROUND|La couleur d’arrière-plan affichée entre les mois.|  
|MCSC_MONTHBK|La couleur d’arrière-plan affichée dans le mois.|  
|MCSC_TEXT|La couleur utilisée pour afficher le texte d’un mois.|  
|MCSC_TITLEBK|La couleur d’arrière-plan affichée dans le titre du calendrier.|  
|MCSC_TITLETEXT|La couleur utilisée pour afficher du texte dans le titre du calendrier.|  
|MCSC_TRAILINGTEXT|La couleur utilisée pour afficher le texte d’en-tête et le jour de fin. Les jours précédents et sont les jours des mois précédents et suivants qui s’affichent dans le calendrier actuel.|  
  
 *ref*  
 A **COLORREF** valeur pour le nouveau paramètre de couleur pour la partie spécifiée du contrôle month calendar.  
  
### <a name="return-value"></a>Valeur de retour  
 A **COLORREF** valeur qui représente le paramètre précédent de la couleur pour la partie spécifiée du contrôle month calendar, en cas de réussite. Dans le cas contraire, ce message retourne -1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView  
 Définit le contrôle de calendrier mois en cours pour afficher la vue spécifiée.  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *dwNewView*|Une des valeurs suivantes qui spécifie un mensuel, annuel, dix ou siècle.<br /><br /> MCMV_MONTH : Affichage de tous les mois<br /><br /> MCMV_YEAR : Vue annuel<br /><br /> MCMV_DECADE : Affichage des dix dernières années<br /><br /> MCMV_CENTURY : Affichage de siècle|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel  
 Définit la date actuellement sélectionnée pour un contrôle month calendar.  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Paramètres  
 *refDateTime*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ou [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet indiquant le contrôle de calendrier sélectionné de mois.  
  
 *pDateTime*  
 Pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à définir en tant que la sélection actuelle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `SetCurSel`, vous pouvez spécifier un `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState  
 Définit l’affichage des jours dans un contrôle month calendar.  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>Paramètres  
 *nMonths*  
 Valeur qui indique le nombre d’éléments présents dans le tableau qui *pStates* pointe vers.  
  
 *pStates*  
 Un pointeur vers un [MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915) tableau de valeurs qui définissent la façon dont le contrôle month calendar doit dessiner chaque jour dans son affichage. Le **MONTHDAYSTATE** type de données est un champ de bits, où chaque bit (1 à 31) représente l’état d’un jour du mois. Si un bit est activé, le jour correspondant s'affiche en gras ; sinon il s'affiche sans l'accentuation.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView  
 Définit le calendrier du mois en cours contrôle à la vue des dix dernières années.  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode utilise le [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue `MCMV_DECADE`, qui représente l’affichage des dix dernières années.  
  
##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek  
 Définit le jour de la semaine à afficher dans la colonne la plus à gauche du calendrier.  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *iDay*  
 Valeur entière représentant le jour doit être définie comme étant le premier jour de la semaine. Cette valeur doit être un des numéros de jour. Consultez [GetFirstDayOfWeek](#getfirstdayofweek) pour obtenir une description des numéros de jour.  
  
 *lpnOld*  
 Un pointeur vers un entier indiquant le premier jour de la semaine précédemment défini.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le premier jour de la semaine précédent est défini sur une valeur autre que celui de **LOCALE_IFIRSTDAYOFWEEK**, qui est le jour est indiqué dans le panneau de configuration de contrôle. Sinon, cette fonction retourne 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount  
 Définit le nombre maximal de jours pouvant être sélectionnés dans un contrôle month calendar.  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 *nombre maximal*  
 La valeur à définir pour représenter le nombre maximal de jours pouvant être sélectionnées.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta  
 Définit la vitesse de défilement d’un contrôle month calendar.  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>Paramètres  
 *iDelta*  
 Le nombre de mois à définir comme la vitesse de défilement du contrôle. Si cette valeur est zéro, le delta de mois est réinitialisé à la valeur par défaut, ce qui correspond au nombre de mois à afficher dans le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 La vitesse de défilement précédente. Si la vitesse de défilement n’a pas été définie précédemment, la valeur de retour est 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView  
 Définit le contrôle de calendrier mois en cours pour afficher la vue du mois.  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode utilise le [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue `MCMV_MONTH`, qui représente la vue du mois.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit la variable, `m_monthCalCtrl`, qui est utilisé pour accéder par programme le contrôle month calendar. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit le contrôle month calendar pour afficher le mois, année, décennie et vues de siècle.  
  
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
 *pMinRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.  
  
 *pMaxRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `SetRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMonthCalCtrl::GetRange](#getrange).  
  
##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange  
 Définit la sélection d’un calendrier du mois contrôle à une plage de dates donnée.  
  
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
 *pMinRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient la date à la fin de la plus basse de la plage.  
  
 *pMaxRange*  
 Un pointeur vers un `COleDateTime` objet, un `CTime` objet, ou `SYSTEMTIME` structure qui contient la date à la fin de la plus élevée de la plage.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014), comme décrit dans le Kit de développement logiciel Windows. Dans l’implémentation MFC de `SetSelRange`, vous pouvez spécifier `COleDateTime` utilisation, un `CTime` l’utilisation, ou un `SYSTEMTIME` d’utilisation de la structure.  
  
##  <a name="settoday"></a>  CMonthCalCtrl::SetToday  
 Définit le contrôle de calendrier pour le jour actuel.  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Paramètres  
 *refDateTime*  
 Une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui contient la date actuelle.  
  
 *pDateTime*  
 Dans la deuxième version, un pointeur vers un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet contenant les informations de date actuelle. Dans la troisième version, un pointeur vers un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient les informations de date actuelle.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMonthCalCtrl::GetToday](#gettoday).  
  
##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView  
 Définit le calendrier du mois en cours contrôle en mode année.  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode utilise le [CMonthCalCtrl::SetCurrentView](#setcurrentview) pour définir la vue `MCMV_YEAR`, qui représente la vue annuelle.  
  
##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq  
 Affiche le mois de contrôle de calendrier au minimum la taille qui affiche un mois.  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bRepaint*  
 Spécifie si le contrôle doit être redessinée. Par défaut, **TRUE**. Si **FALSE**, aucune mise à jour se produit.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle month calendar a une taille minimale ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appel de `SizeMinReq` affiche le contrôle de calendrier du mois entier pour le calendrier d’un mois.  
  
##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin  
 Pour le contrôle calendrier du mois en cours, calcule le plus petit rectangle qui peut contenir tous les calendriers qui tiennent dans un rectangle spécifié.  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *lpRect*|Pointeur vers un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui définit un rectangle qui contient le nombre souhaité de calendriers.|  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui définit un rectangle dont la taille est inférieure ou égale au rectangle défini par le *lpRect* paramètre.  
  
### <a name="remarks"></a>Notes  
 Cette méthode calcule le nombre de calendriers peut être contenue dans le rectangle spécifié par le *lpRect* paramètre, puis retourne le plus petit rectangle pouvant contenir ce nombre de calendriers. En effet, cette méthode réduit le rectangle spécifié adapte exactement le nombre souhaité de calendriers.  
  
 Cette méthode envoie le [MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [MFC exemple CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl, classe](../../mfc/reference/cdatetimectrl-class.md)
