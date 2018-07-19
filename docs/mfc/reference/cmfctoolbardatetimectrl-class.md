---
title: Cmfctoolbardatetimectrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94f275ae65b8c3135a110e249b0521194083683c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854081"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Cmfctoolbardatetimectrl, classe
Un bouton de barre d’outils qui contient un contrôle de sélecteur de date et d’heure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Construit un objet `CMFCToolBarDateTimeCtrl`.|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Spécifie si un utilisateur permet d’étendre le bouton au cours de personnalisation. (Substitue [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours. (Substitue [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Réservé à un usage ultérieur.|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copie le texte à partir du bouton de barre d’outils dans un menu.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Récupère le premier `CMFCToolBarDateTimeCtrl` objet dans l’application qui possède l’ID de commande spécifiée.|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Retourne un pointeur vers le contrôle de sélecteur de date et d’heure.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Récupère le handle de fenêtre qui est associé au bouton de barre d’outils. (Substitue [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtient l’heure sélectionnée à partir d’un contrôle de sélecteur de date et l’heure et le place dans une certaine [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure.|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Retourne l’heure sélectionnée à partir du bouton de contrôle de sélecteur de temps qui a un ID de commande spécifié.|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton est affichée lorsqu’un utilisateur sélectionne le bouton. (Substitue [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Spécifie si le bouton traite le [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) message. (Substitue [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Appelé par le framework lorsque le bouton est ajouté à un **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage. (Substitue [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Appelé par le framework lorsque l’utilisateur clique sur le contrôle. (Substitue [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_CTLCOLOR. (Substitue [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés. (Substitue [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le framework lorsque la police globale a été modifiée. (Substitue [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Appelé par le framework lorsque la barre d’outils parent se déplace. (Substitue [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Appelé par le framework lorsque le bouton est visible ou invisible. (Substitue [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Appelé par l’infrastructure lors de la barre d’outils parent change sa taille ou la position et cette modification entraîne le bouton Modifier la taille. (Substitue [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Appelé par l’infrastructure lors de la barre d’outils parent met à jour son texte d’info-bulle. (Substitue [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Lit de cet objet à partir d’une archive ou écrit dans une archive, (remplace [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Définit le style du bouton de barre d’outils. (Substitue [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Définit la date et l’heure dans le contrôle de sélecteur d’heure.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Définit la date et l’heure dans toutes les instances du contrôle de sélecteur de temps qui ont un ID de commande spécifié.|  
  
## <a name="remarks"></a>Notes  
 Pour obtenir un exemple montrant comment utiliser un contrôle de sélecteur de date et d’heure, consultez l’exemple de projet ToolbarDateTimePicker. Pour plus d’informations sur la façon d’ajouter des boutons de contrôle, consultez [procédure pas à pas : placer le contrôle sur la barre de d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched  
 Spécifie si un utilisateur permet d’étendre le bouton au cours de personnalisation.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne la valeur TRUE.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le framework n’autorise pas l’utilisateur étirer un bouton de barre d’outils au cours de personnalisation. Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en autorisant l’utilisateur étirer un bouton de barre d’outils de date et d’heure au cours de personnalisation.  
  
##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl  
 Crée et initialise un [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) objet.  
  
```  
CMFCToolBarDateTimeCtrl(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=0,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiID*  
 L’ID du contrôle.  
  
 [in] *iImage*  
 L’index de l’image dans la barre d’outils `CMFCToolBarImages` objet.  
  
 [in] *dwStyle*  
 Le style de la `CMFCToolBarDateTimeCtrlImpl` fenêtre qui est créé quand un utilisateur clique sur le bouton.  
  
 [in] *iLargeur Argument de type*  
 Largeur du contrôle, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cet objet est initialisé à la date et heure système. Le style de fenêtre d’interne `CMFCToolBarDateTimeCtrlImpl` objet inclut le *dwStyle* paramètre et les styles WS_CHILD et WS_VISIBLE. Vous ne pouvez pas modifier ces styles à l’aide de `CMFCToolBarDateTimeCtrl::SetStyle`. Utilisez `SetStyle` pour modifier le style de la `CMFCToolBarDateTimeCtrl` contrôle.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCToolBarDateTimeCtrl` classe. Cet extrait de code fait partie de la [exemple de barre d’outils Date Time Picker](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom  
 Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *src*  
 Une référence au bouton de la source à partir duquel copier.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être de type `CMFCToolBarDateTimeCtrl`.  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 Copie le texte à partir du bouton de barre d’outils dans un menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bouton de menu*  
 Une référence au bouton de menu cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne la valeur TRUE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) en chargeant la ressource de chaîne qui est associée à l’ID de commande du contrôle. Pour plus d’informations sur les ressources de type chaîne, consultez [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).  
  
##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd  
 Récupère le premier `CMFCToolBarDateTimeCtrl` objet dans l’application qui possède l’ID de commande spécifiée.  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmd*  
 ID de commande du bouton à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 La première `CMFCToolBarDateTimeCtrl` objet dans l’application qui a l’ID de commande spécifié, ou NULL si aucun `CMFCToolBarDateTimeCtrl` objets ont des ID de commande spécifié.  
  
### <a name="remarks"></a>Notes  
 Cette méthode d’utilitaire partagé est utilisée par les méthodes telles que [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) et [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) pour définir ou obtenir la date et heure de toutes les instances de l’heure contrôle de sélecteur qui ont un ID de commande spécifié.  
  
##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 Retourne un pointeur vers le contrôle de sélecteur de date et d’heure.  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le contrôle de sélecteur de date et heure ; ou NULL si le contrôle n’existe pas.  
  
### <a name="remarks"></a>Notes  
 Le `CMFCToolBarDateTimeCtrl` classe initialise le `m_pWndDateTime` membre de données lorsque vous insérez un `CMFCToolBarDateTimeCtrl` objet dans une barre d’outils.  
  
##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd  
 Récupère le handle de fenêtre qui est associé au bouton de barre d’outils.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de fenêtre qui est associé au bouton de barre d’outils de date et d’heure.  
  
### <a name="remarks"></a>Notes  
 Cette méthode remplace la [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) (méthode).  
  
##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime  
 Obtient l’heure sélectionnée à partir de la date associée et le contrôle de sélecteur de temps et le place dans une certaine [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *timeDest*  
 Dans la première surcharge, un [COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui recevra les informations d’heure système. Dans la seconde surcharge, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui recevra les informations d’heure système.  
  
 [out] *pTimeDest*  
 Un pointeur vers le [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui doit recevoir les informations d’heure système. Ne doit pas être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Dans la première surcharge, différent de zéro si l’heure est correctement écrite dans le [COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md) objet ; sinon 0. Dans les deuxième et troisième surcharges, la valeur de retour est une valeur DWORD qui est égal au membre dwFlag qui a été défini dans le [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) structure.  
  
### <a name="remarks"></a>Notes  
 La méthode indique le [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) structure dwFlags de membre pour indiquer si le sélecteur de date et d’heure est défini sur une date et une heure. Si la valeur est égale à GDT_NONE, le contrôle est défini sur `no date` état et utilise le style DTS_SHOWNONE. Si la valeur retournée est égale à GDT_VALID, l’heure système est correctement stockée dans l’emplacement de destination.  
  
##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll  
 Retourne la période sélectionnée par l’utilisateur à partir du bouton de contrôle de sélecteur de temps qui a un ID de commande spécifié.  
  
```  
static BOOL GetTimeAll(
    UINT uiCmd,  
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeDest);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmd*  
 Spécifie l’ID de commande. d’un bouton de barre d’outils  
  
 [out] *timeDest*  
 Dans la première surcharge, un [COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui recevra les informations d’heure système. Dans la seconde surcharge, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui recevra les informations d’heure système.  
  
 [out] *pTimeDest*  
 Un pointeur vers le [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui doit recevoir les informations d’heure système. Ne doit pas être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le framework ne peut pas trouver un bouton de barre d’outils qui correspond à l’ID de commande *uiCmd*, la valeur de retour est zéro dans la première surcharge et GDT_NONE dans les autres surcharges. Si le bouton de barre d’outils est trouvé, la valeur de retour est identique à la valeur de retour d’un appel à [CMFCToolBarDateTimeCtrl::GetTime](#gettime) sur ce bouton. A retourner la valeur de zéro ou GDT_NONE peut se produire lorsque le bouton est trouvé, ce qui indique que l’appel à `GetTime` n’a pas retourné une date valide pour une raison quelconque.  
  
### <a name="remarks"></a>Notes  
 Cette méthode recherche un bouton de barre d’outils qui contient les ID de commande spécifié et les appels [CMFCToolBarDateTimeCtrl::GetTime](#gettime) méthode sur ce bouton.  
  
##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder  
 Détermine si une bordure du bouton est affichée lorsqu’un utilisateur sélectionne le bouton.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si un bouton affiche sa bordure lorsque sélectionné ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne une valeur différente de zéro si le contrôle est visible.  
  
##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand  
 Spécifie si le bouton traite le [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) message.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iNotifyCode*  
 Le message de notification qui est associé à la commande.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le bouton traite le message WM_COMMAND, ou FALSE pour indiquer que le message doit être géré par la barre d’outils parent.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’il est sur le point d’envoyer un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) message vers la fenêtre parente.  
  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant le [DTN_DATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761737) notification. Il met à jour l’état interne de temps et met à jour la propriété de temps de tous les `CMFCToolBarDateTimeCtrl` objets avec le même ID de commande.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 Appelé par le framework lorsque le bouton est ajouté à un **personnaliser** boîte de dialogue.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), par copie des propriétés à partir de la première date et l’heure de contrôle dans la barre d’outils quelconque qui a le même ID de commande en tant que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a un contrôle de date et d’heure qui a le même ID de commande en tant que cet objet.  
  
 Pour plus d’informations sur la **personnaliser** boîte de dialogue, consultez [cmfctoolbarscustomizedialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndParent*  
 La nouvelle fenêtre parente.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant interne `CMFCToolBarDateTimeCtrlImpl` objet.  
  
##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick  
 Appelé par le framework lorsque l’utilisateur clique sur le contrôle.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
 Non utilisé.  
  
 [in] *bDelay*  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton traite le message de clic ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de la classe de base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en retournant une valeur différente de zéro si le texte interne `CMFCToolBarDateTimeCtrlImpl` objet est visible.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor  
 Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_CTLCOLOR.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pDC*  
 Le contexte de périphérique qui affiche le bouton.  
  
 [in] *nCtlColor*  
 Non utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le pinceau global que l’infrastructure utilise pour peindre l’arrière-plan du bouton.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de la classe de base, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), en définissant le texte et d’arrière-plan du contexte de périphérique fourni au texte global des couleurs et couleurs d’arrière-plan, respectivement.  
  
 Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [afx_global_data, Structure](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 Appelé par le framework lorsque la police globale a été modifiée.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en modifiant la police du contrôle à celle de la police globale.  
  
 Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [afx_global_data, Structure](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove  
 Appelé par le framework lorsque la barre d’outils parent se déplace.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de classe par défaut ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position d’interne `CMFCToolBarDateTimeCtrlImpl` objet.  
  
##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow  
 Appelé par le framework lorsque le bouton est visible ou invisible.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bShow*  
 Spécifie si le bouton est visible. Si ce paramètre est TRUE, le bouton est visible. Sinon, le bouton n’est pas visible.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* a la valeur TRUE. Sinon, cette méthode masque le bouton.  
  
##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize  
 Appelé par l’infrastructure lors de la barre d’outils parent change sa taille ou la position et cette modification entraîne le bouton Modifier la taille.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iSize*  
 La nouvelle largeur du bouton, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode substitue l’implémentation de classe par défaut ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) en mettant à jour la taille et la position d’interne `CMFCToolBarDateTimeCtrlImpl` objet.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 Appelé par l’infrastructure lors de la barre d’outils parent met à jour son texte d’info-bulle.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndParent*  
 La fenêtre parente.  
  
 [in] *iButtonIndex*  
 Index de base zéro du bouton dans la collection de boutons de parent.  
  
 [in] *wndToolTip*  
 Le contrôle qui affiche le texte d’info-bulle.  
  
 [out] *str*  
 Un `CString` objet qui reçoit le texte d’info-bulle mis à jour.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la méthode met à jour le texte d’info-bulle ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte d’info-bulle est associé au bouton. Si le bouton n’est pas ancré horizontalement, cette méthode ne fait rien et retourne FALSE.  
  
##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime  
 Définit la date et l’heure dans le contrôle de sélecteur d’heure.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *transfertnouvelle*  
 Dans la première version, une référence à un [COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui contient l’heure défini pour le contrôle. Dans la deuxième version, un pointeur vers un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui contient l’heure défini pour le contrôle.  
  
 [in] *pTimeNew*  
 Un pointeur vers le [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient l’heure défini pour le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Définit l’heure dans un contrôle de sélecteur de date et d’heure en appelant [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).  
  
##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll  
 Définit la date et l’heure dans toutes les instances du contrôle de sélecteur de temps qui ont un ID de commande spécifié.  
  
```  
static BOOL SetTimeAll(
    UINT uiCmd,  
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmd*  
 Spécifie l’ID de commande. d’un bouton de barre d’outils  
  
 [in] *transfertnouvelle*  
 Dans la première version, un [COleDateTime, classe](../../atl-mfc-shared/reference/coledatetime-class.md) objet qui contient l’heure défini pour le contrôle. Dans la deuxième version, un pointeur vers un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet qui contient l’heure défini pour le contrôle.  
  
 [in] *pTimeNew*  
 Un pointeur vers le [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) structure qui contient l’heure défini pour le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Recherche un bouton de barre d’outils avec l’ID de commande spécifié et définit l’heure dans un contrôle de sélecteur de date et d’heure en appelant [CMFCToolBarDateTimeCtrl::SetTime](#settime).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfctoolbarbutton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)



